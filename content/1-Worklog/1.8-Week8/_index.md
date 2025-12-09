---
title: "Week 8 Worklog"
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Objectives for Week 8:

- Clearly understand the architecture, advantages, and core components of the serverless compute service **AWS Lambda**.

[Image of AWS Lambda architecture components]

- Master creating, deploying, and managing Lambda functions.
- Master the role and configuration of **Amazon API Gateway** to create RESTful APIs.
- Practice building a simple Serverless application by integrating Lambda and API Gateway.

### Tasks to be implemented this week:

| Day | Task                                                                                                                                                                                                                                                                                                          | Start Date | Completion Date | Resources                                 |
| :-- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--------- | :-------------- | :---------------------------------------- |
| 2   | - Read and understand **AWS Lambda** architecture (Function, Runtime, Handler, Execution Role). <br> - Compare Serverless (Lambda) with Compute (EC2). <br> - **Practice:** Create and deploy a simple Lambda function (e.g., print "Hello World").                                                           | 27/10/2025 | 27/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Learn about the **Event-Driven** mechanism in Lambda. <br> - **Practice:** <br>&emsp; + Configure a Trigger for Lambda to be activated by an S3 event (e.g., file upload). <br>&emsp; + Configure Lambda to read/write data from DynamoDB (using IAM Role).                                                 | 28/10/2025 | 28/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn about **Amazon API Gateway** service (REST API, Stage, Resource, Method). <br> - **Practice:** Create a new REST API on API Gateway. <br> - Define basic Resources and Methods (e.g., GET /items, POST /items).                                                                                       | 29/10/2025 | 29/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn about **Integration Type** (Lambda Proxy Integration) between API Gateway and Lambda. <br> - **Practice:** <br>&emsp; + Connect Method POST /items of API Gateway with the Lambda function created on day 2. <br>&emsp; + Deploy the API to a Stage (e.g., `prod`) and test via the public URL.       | 30/10/2025 | 30/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Security, Monitoring & Cleanup:** <br> - Learn about CORS (Cross-Origin Resource Sharing) and how to enable it on API Gateway. <br> - **Practice:** <br>&emsp; + Enable CORS for the API. <br>&emsp; + Check Lambda Logs on CloudWatch. <br>&emsp; + Delete API Gateway, then delete the Lambda function. | 31/10/2025 | 31/10/2025      | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in Week 8:

- **Lambda Fundamentals:** Clearly understood the Serverless model, proficient in creating, configuring, and managing Lambda functions (Function, Role, Runtime).
- **Event-Driven:** Understood how Lambda operates based on events and practiced integrating with other services like S3 and DynamoDB.
- **API Gateway:** Mastered API Gateway architecture (Resource, Method, Stage) and the ability to create RESTful APIs.
- **Serverless Construction:** Successfully deployed a basic Serverless architecture (**API Gateway -> Lambda -> DynamoDB**), a popular architecture pattern on AWS.
- **Security & Cleanup:** Grasped how to manage Lambda Logs via CloudWatch and performed Serverless resource cleanup.
