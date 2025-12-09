---
title: "Blog 3"
date: 2025-07-10
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Artificial Intelligence: Supercharge your AI workflows by connecting to SageMaker Studio from Visual Studio Code

**by Durga Sury, Raj Bagwe, Sri Aakash Mandavilli, and Edward Sun on 10 JUL 2025**
_Categories: Advanced (300), Amazon SageMaker Studio, Technical How-to_

---

AI developers and machine learning (ML) engineers can now use the capabilities of Amazon SageMaker Studio directly from their local Visual Studio Code (VS Code). With this capability, you can use your customized local VS Code setup, including AI-assisted development tools, custom extensions, and debugging tools while accessing compute resources and your data in SageMaker Studio. By accessing familiar model development features, data scientists can maintain their established workflows, preserve their productivity tools, and seamlessly develop, train, and deploy machine learning, deep learning and generative AI models.

In this post, we show you how to remotely connect your local VS Code to SageMaker Studio development environments to use your customized development environment while accessing Amazon SageMaker AI compute resources.

The local integrated development environment (IDE) connection capability delivers three key benefits for developers and data scientists:

- **Familiar development environment with scalable compute:** Work in your familiar IDE environment while harnessing the purpose-built model development environment of SageMaker AI. Keep your preferred themes, shortcuts, extensions, productivity, and AI tools while accessing SageMaker AI features.
- **Simplify operations:** With a few clicks, you can minimize the complex configurations and administrative overhead of setting up remote access to SageMaker Studio spaces. The integration provides direct access to Studio spaces from your IDE.
- **Enterprise grade security:** Benefit from secure connections between your IDE and SageMaker AI through automatic credentials management and session maintenance. In addition, code execution remains within the controlled boundaries of SageMaker AI.

This feature bridges the gap between local development preferences and cloud-based machine learning resources, so that teams can improve their productivity while using the features of Amazon SageMaker AI.

## Solution overview

The following diagram showcases the interaction between your local IDE and SageMaker Studio spaces.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-1.png)

The solution architecture consists of three main components:

- **Local computer:** Your development machine running VS Code with AWS Toolkit extension installed.
- **SageMaker Studio:** A unified, web-based ML development environment to seamlessly build, train, deploy, and manage machine learning and analytics workflows at scale using integrated AWS tools and secure, governed access to your data.
- **AWS Systems Manager:** A secure, scalable remote access and management service that enables seamless connectivity between your local VS Code and SageMaker Studio spaces to streamline ML development workflows.

The connection flow supports two options:

- **Direct launch (deep link):** Users can initiate the connection directly from the SageMaker Studio web interface by choosing Open in VS Code, which automatically launches their local VS Code instance.
- **AWS Toolkit connection:** Users can connect through AWS Toolkit extension in VS Code by browsing available SageMaker Studio spaces and selecting their target environment.

In addition to the preceding, users can also connect to their space directly from their IDE terminal using SSH. For instructions on connecting using SSH, refer to documentation here.

After connecting, developers can:

- Use their custom VS Code extensions and tools
- Remotely access and use their space’s storage
- Run their AI and ML workloads in SageMaker compute environments
- Work with notebooks in their preferred IDE
- Maintain the same security parameters as the SageMaker Studio web environment

## Solution implementation

### Prerequisites

To try the remote IDE connection, you must meet the following prerequisites:

- You have access to a SageMaker Studio domain with connectivity to the internet. For domains set up in VPC-only mode, your domain should have a route out to the internet through a proxy, or a NAT gateway. If your domain is completely isolated from the internet, see Connect to VPC with subnets without internet access for setting up the remote connection. If you do not have a Studio domain, you can create one using the quick setup or custom setup option.
- You have permissions to update the SageMaker Studio domain or user execution role in AWS Identity and Access Management (IAM).
- You have the latest stable VS Code with Microsoft Remote SSH (version 0.74.0 or later), and AWS Toolkit extension (version v3.68.0 or later) installed on your local machine. Optionally, if you want to connect to SageMaker spaces directly from VS Code, you should be authenticated to access AWS resources using IAM or AWS IAM Identity Center credentials. See the administrator documentation for AWS Toolkit authentication support.
- You use compatible SageMaker Distribution images (2.7+ and 3.1+) for running SageMaker Studio spaces, or a custom image.
- If you’re initiating the connection from the IDE, you already have a user profile in the SageMaker Studio domain you want to connect to, and the spaces are already created using the Studio UI or through APIs. The AWS Toolkit does not allow creation or deletion of spaces.

### Set up necessary permissions

We’ve launched the StartSession API for remote IDE connectivity. Add the sagemaker:StartSession permission to your user’s role so that they can remotely connect to a space.

For the deep-linking experience, the user starts the remote session from the Studio UI. Hence, the domain default execution role, or the user’s execution role should allow the user to call the StartSession API. Modify the permissions on your domain or user execution role by adding the following policy statement:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "RestrictStartSessionOnSpacesToUserProfile",
      "Effect": "Allow",
      "Action": ["sagemaker:StartSession"],
      "Resource": "arn:*:sagemaker:${aws:Region}:${aws:AccountId}:space/${sagemaker:DomainId}/*",
      "Condition": {
        "ArnLike": {
          "sagemaker:ResourceTag/sagemaker:user-profile-arn": "arn:*:sagemaker:${aws:Region}:${aws:AccountId}:user-profile/${sagemaker:DomainId}/${sagemaker:UserProfileName}"
        }
      }
    }
  ]
}
```

If you’re initializing the connection to SageMaker Studio spaces directly from VS Code, your AWS credentials should allow the user to list the spaces, start or stop a space, and initiate a connection to a running space. Make sure that your AWS credentials allow the following API actions:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "sagemaker:ListSpaces",
        "sagemaker:DescribeSpace",
        "sagemaker:UpdateSpace",
        "sagemaker:ListApps",
        "sagemaker:CreateApp",
        "sagemaker:DeleteApp",
        "sagemaker:DescribeApp",
        "sagemaker:StartSession",
        "sagemaker:DescribeDomain",
        "sagemaker:AddTags"
      ],
      "Resource": "*"
    }
  ]
}
```

This initial IAM policy provides a quick-start foundation for testing SageMaker features. Organizations can implement more granular access controls using resource Amazon Resource Name (ARN) constraints or attribute-based access control (ABAC). With the introduction of the StartSession API, you can restrict access by defining space ARNs in the resource section or implementing condition tags according to your specific security needs, as shown in the following example.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowRemoteAccessByTag",
      "Effect": "Allow",
      "Action": ["sagemaker:StartSession"],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "aws:ResourceTag/User": "<user-identifier>"
        }
      }
    }
  ]
}
```

### Enable remote connectivity and launch VS Code from SageMaker Studio

To connect to a SageMaker space remotely, the space must have remote access enabled.
Before running a space on the Studio UI, you can toggle Remote access on to enable the feature, as shown in the following screenshot.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/10/screenshot-enable-remote-access-outline-1.png)

After the feature is enabled, choose Run space to start the space. After the space is running, choose Open in VS Code to launch VS Code.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/10/screenshot-open-vs-code-arrow.png)

The first time you choose this option, you’ll be prompted by your browser to confirm opening VS Code. Select the checkbox Always allow studio to confirm and then choose Open Visual Studio Code.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-4.jpeg)

This will open VS Code, and you will be prompted to update your SSH configuration. Choose Update SSH config to complete the connection. This is also a one-time setup, and you will not be prompted for future connections.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-5-300x220.jpeg)

On successful connection, a new window launches that is connected to the SageMaker Studio space and has access to the Studio space’s storage.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-6.jpeg)

### Connect to the space from VS Code

Using the AWS Toolkit, you can list the spaces, start, connect to a space, or connect to a running space that has remote connection enabled. If a running space doesn’t have remote connectivity enabled, you can stop the space from the AWS Toolkit and then select the Connect icon to automatically turn on remote connectivity and start the space. The following section describes the experience in detail.

After you’re authenticated into AWS, from AWS Toolkit, access the AWS Region where your SageMaker Studio domain is. You will now see a SageMaker AI section. Choose the SageMaker AI section to list the spaces in your Region. If you’re connected using IAM, the toolkit lists the spaces across domains and users in your Region. See the [Optional] Filter spaces to a specific domain or user below on instructions to view spaces for a particular user profile. For Identity Center users, the list is already filtered to display only the spaces owned by you.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-7.jpeg)

After you identify the space, choose the connectivity icon as shown in the screenshot below to connect to the space.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-8.jpeg)

**Optional: Filter spaces to a specific domain or user**

When connecting to an account using IAM, you will see a list of spaces in the account and region. This can be overwhelming if the account has tens or hundreds of domains, users and spaces. The toolkit provides a filter utility that helps you quickly filter the list of spaces to a specific user profile or a list of user profiles.
Next to SageMaker AI, choose the filter icon as shown in the following screenshot.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-9.jpeg)

You will now see a list of user profiles and domains. Scroll through the list or enter user profile or domain name, and then select or unselect to filter the list of spaces by domain or user profile.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-10.jpeg)

## Use cases

Following use cases demonstrate how AI developers and machine learning (ML) engineers can use local integrated development environment (IDE) connection capability.

### Connecting to a notebook kernel

After you’re connected to the space, you can start creating and running notebooks and scripts right from your local development environment. By using this method, you can use the managed infrastructure provided by SageMaker for resource-intensive AI tasks while coding in a familiar environment. You can run notebook cells on your SageMaker Distribution or custom image kernels, and can choose the IDE that maximizes your productivity. Use the following steps to create and connect your notebook to a remote kernel –

1.  On your VS Code file explorer, choose the plus (+) icon to create a new file, name it remote-kernel.ipynb.
2.  Open the notebook and run a cell (for example, print ("Hello from remote IDE"). VS Code will show a pop-up for installing the Python and Jupyter extension.
3.  Choose Install/Enable suggested extensions.
4.  After the extensions are installed, VS Code will automatically launch the kernel selector. You can also choose Select Kernel on the right to view the list of kernels.
5.  For the next steps, follow the directions for the space you’re connected to.

**Code Editor spaces:**
Select Python environments… and choose from a list of provided Python environments. After you are connected, you can start running the cells in your notebook.

**JupyterLab spaces:**
Select the Existing Jupyter Server… option to have the same kernel experience as the JupyterLab environment.
If this is the first time connecting to JupyterLab spaces, you will need to configure the Jupyter server to view the same kernels as the remote server using the following steps.

1.  Choose Enter the URL of the running Jupyter Server and enter http://localhost:8888/jupyterlab/default/lab as the URL and press Enter.
2.  Enter a custom server display name, for example, JupyterLab Space Default Server and press Enter.You will now be able to view the list of kernels that’s available on the remote Jupyter server. For consequent connections, this display name will be available for you to choose from when you select the existing Jupyter server option.

The following graphic shows the entire workflow. In this example, we’re running a JupyterLab space with the SageMaker Distribution image, so we can view the list of kernels available in the image.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/14/python-kernels.gif)

You can choose the kernel of your choice, for example, the Python 3 kernel, and you can start running the notebook cells on the remote kernel. With access to the SageMaker managed kernels, you can now focus on model development rather than infrastructure and runtime management, while using the development environment you know and trust.

## Best practices and guardrails

- Follow the principle of least privilege when allowing users to connect remotely to SageMaker Studio spaces applications. SageMaker Studio supports custom tag propagation, we recommend tagging each user with a unique identifier and using the tag to allow the StartSession API to only their private applications.
- As an administrator, if you want to disable this feature for your users, you can enforce it using the sagemaker:RemoteAccess condition key. The following is an example policy.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowCreateSpaceWithRemoteAccessDisabled",
      "Effect": "Allow",
      "Action": ["sagemaker:CreateSpace", "sagemaker:UpdateSpace"],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "sagemaker:RemoteAccess": ["DISABLED"]
        }
      }
    },
    {
      "Sid": "AllowCreateSpaceWithNoRemoteAccess",
      "Effect": "Allow",
      "Action": ["sagemaker:CreateSpace", "sagemaker:UpdateSpace"],
      "Resource": "*",
      "Condition": {
        "Null": {
          "sagemaker:RemoteAccess": "true"
        }
      }
    }
  ]
}
```

- When connecting remotely to the SageMaker Studio spaces from your local IDE, be aware of bandwidth constraints. For optimal performance, avoid using the remote connection to transfer or access large datasets. Instead, use data transfer methods built for cloud and in-place data processing to facilitate a smooth user experience. We recommend an instance with at least 8 GB of storage to start with, and the SageMaker Studio UI will throw an exception if you choose a smaller instance.

## Cleanup

If you have created a SageMaker Studio domain for the purposes of this post, remember to delete the applications, spaces, user profiles, and the domain. For instructions, see Delete a domain.
For the SageMaker Studio spaces, use the idle shutdown functionality to avoid incurring charges for compute when it is not in use.

## Conclusion

The remote IDE connection feature for Amazon SageMaker Studio bridges the gap between local development environments and powerful ML infrastructure of SageMaker AI. With direct connections from local IDEs to SageMaker Studio spaces, developers and data scientists can now:

- Maintain their preferred development environment while using the compute resources of SageMaker AI
- Use custom extensions, debugging tools, and familiar workflows
- Access governed data and ML resources within existing security boundaries
- Choose between convenient deep linking or AWS Toolkit connection methods
- Operate within enterprise-grade security controls and permissions

This integration minimizes the productivity barriers of context switching while facilitating secure access to SageMaker AI resources. Get started today with SageMaker Studio remote IDE connection to connect your local development environment to SageMaker Studio and experience streamlined ML development workflows using your familiar tools while the powerful ML infrastructure of SageMaker AI.

## About the authors

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-12-100x100.jpeg)

**Durga Sury** is a Senior Solutions Architect at Amazon SageMaker, where she helps enterprise customers build secure and scalable AI/ML systems. When she’s not architecting solutions, you can find her enjoying sunny walks with her dog, immersing herself in murder mystery books, or catching up on her favorite Netflix shows.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-13.jpeg)

**Edward Sun** is a Senior SDE working for SageMaker Studio at Amazon Web Services. He is focused on building interactive ML solution and simplifying the customer experience to integrate SageMaker Studio with popular technologies in data engineering and ML landscape. In his spare time, Edward is big fan of camping, hiking, and fishing, and enjoys spending time with his family.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-14-100x119.jpeg)

**Raj Bagwe** is a Senior Solutions Architect at Amazon Web Services, based in San Francisco, California. With over 6 years at AWS, he helps customers navigate complex technological challenges and specializes in Cloud Architecture, Security and Migrations. In his spare time, he coaches a robotics team and plays volleyball. He can be reached at X handle @rajesh_bagwe.

![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2025/07/09/ML-19130-15-100x133.jpeg)

**Sri Aakash Mandavilli** is a Software Engineer on the Amazon SageMaker Studio team, where he has been building innovative products since 2021. He specializes in developing various solutions across the Studio service to enhance the machine learning development experience. Outside of work, SriAakash enjoys staying active through hiking, biking, and taking long walks.
