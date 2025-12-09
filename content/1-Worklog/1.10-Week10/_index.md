---
title: "Week 10 Worklog"
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Objectives for Week 10:

- Clearly understand the role and operation of the **Amazon Simple Queue Service (SQS)** message queue service (Standard & FIFO).
- Master the **Publish/Subscribe** architecture with the **Amazon Simple Notification Service (SNS)** notification service.

[Image of AWS SNS architecture]

- Proficient in creating and configuring **AWS Step Functions** state machines to orchestrate AWS services.
- Practice building an asynchronous workflow using SQS, SNS, and Lambda.

### Tasks to be implemented this week:

| Day | Task                                                                                                                                                                                                                                                                                                                    | Start Date | Completion Date | Resources                                 |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------- |
| 2   | - Read and understand **Amazon SQS** (Message Queue) architecture and the difference between Standard Queue and FIFO Queue. <br> - **Practice:** Create an SQS Standard Queue, manually send and receive messages via Console.                                                                                          | 10/11/2025 | 10/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Learn about **Amazon SNS** notification service (Topic, Subscriber) and Pub/Sub model. <br> - **Practice:** <br>&emsp; + Create an SNS Topic. <br>&emsp; + Create SQS Queue and Lambda function (from Week 8) as Subscribers for this Topic. <br>&emsp; + Send message to Topic and verify if SQS/Lambda received it. | 11/11/2025 | 11/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn about **AWS Step Functions** (State Machine, Task State, Choice State). <br> - **Practice:** <br>&emsp; + Create a new Lambda function (e.g., `ProcessStep1`). <br>&emsp; + Create a simple State Machine (with only one Task step) to invoke this Lambda function.                                             | 12/11/2025 | 12/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn how **Step Functions** orchestrate logic flow (Sequence, Choice, Parallel). <br> - **Practice:** Expand the created State Machine: <br>&emsp; + Add a `Choice` step based on input results. <br>&emsp; + Integrate SQS (e.g., send message to queue if flow goes a certain branch).                             | 13/11/2025 | 13/11/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Resource Cleanup & General Integration:** <br> - **Practice:** <br>&emsp; + Delete State Machine, SQS Queue, SNS Topic. <br>&emsp; + Review how these services (SQS, SNS, Step Functions) solve asynchronous communication and decoupling issues in applications.                                                   | 14/11/2025 | 14/11/2025      | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in Week 10:

- **Message Queues:** Clearly understood the role of SQS in **decoupling** and **buffering** applications. Proficient in sending/receiving messages.
- **Pub/Sub Model:** Grasped the **SNS** mechanism to efficiently distribute messages to multiple Subscribers.
- **Workflow Orchestration:** Clearly understood how **Step Functions** help orchestrate other AWS services into an organized and easily monitored workflow.
- **Asynchronous System Construction:** Capable of designing application architecture using these application integration services to increase flexibility and scalability.
