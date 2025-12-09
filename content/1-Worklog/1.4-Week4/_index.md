---
title: "Week 4 Worklog"
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Objectives for Week 4:

- Clearly understand the role, architecture, and durability of the **Amazon S3** service.
- Master creating, managing **Buckets**, and applying security policies such as **Bucket Policy**.
- Master S3 storage classes (**Standard, IA, Glacier**) and how to use **Lifecycle Rules** to optimize costs.
- Practice deploying a static website (**Static Website Hosting**) on S3.

### Tasks to be implemented this week:

| Day | Task                                                                                                                                                                                                                                                                                             | Start Date | Completion Date | Resources                                 |
| :-- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------- |
| 2   | - Read and understand the basic architecture of **Amazon S3** (Object, Key, Bucket, Region). <br> - Learn security features: Block Public Access, Access Control List (ACL). <br> - **Practice:** Create a new S3 Bucket and customize Block Public Access settings.                             | 29/09/2025 | 29/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Learn about S3 **Storage Classes** (Standard, Standard-IA, One Zone-IA, Glacier, Deep Archive). <br> - Learn about **Lifecycle Rules** to automatically transition between storage classes. <br> - **Practice:** Configure Lifecycle Rule for a Bucket, transition old objects to Standard-IA. | 30/09/2025 | 30/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn about **Versioning** feature and how to restore objects. <br> - Learn about **Bucket Policy** to manage centralized access. <br> - **Practice:** Enable Versioning for a Bucket and try deleting/restoring an object.                                                                    | 01/10/2025 | 01/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn about **Static Website Hosting** feature on S3. <br> - **Practice:** <br>&emsp; + Upload HTML/CSS/JS files (Index.html & Error.html). <br>&emsp; + Enable Static Website Hosting and set up Bucket Policy to allow public access. <br>&emsp; + Access the website via the S3 Endpoint.   | 02/10/2025 | 02/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Cleanup and S3 CLI Review:** <br> - **Practice:** <br>&emsp; + Use **AWS CLI** to upload/download/sync data with S3 (`aws s3 cp`, `aws s3 sync`). <br>&emsp; + **Clean up resources:** Disable Versioning, delete all objects (including old versions), then delete the Bucket.              | 03/10/2025 | 03/10/2025      | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in Week 4:

- **S3 Management:** Clearly understood and manually created, configured, and managed S3 Buckets. Grasped the role of **Block Public Access** and **ACL**.
- **Cost Optimization:** Mastered S3 **Storage Classes** and learned how to use **Lifecycle Rules** to automatically transition data to less expensive storage classes.
- **Security & Management:** Successfully practiced enabling/disabling **Versioning** and applying **Bucket Policy** to control public and IAM User access.
- **Real-world Application:** Successfully deployed a static website on S3 and accessed it via the public Endpoint.
- **CLI Operations:** Proficient in using AWS CLI to manage data on S3 (upload, download, sync).
