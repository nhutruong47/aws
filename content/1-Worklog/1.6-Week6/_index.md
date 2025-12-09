---
title: "Week 6 Worklog"
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Objectives for Week 6:

- Clearly understand the architecture and advantages of the **Amazon DynamoDB** NoSQL database (Key-Value/Document).
- Master creating, managing DynamoDB tables, and using Index types (GSI/LSI).
- Master the role of **Amazon ElastiCache** in accelerating application response speeds.
- Practice creating and configuring ElastiCache Clusters (Redis/Memcached).

### Tasks to be implemented this week:

| Day | Task                                                                                           | Start Date | Completion Date | Resources |
| :-- | :--------------------------------------------------------------------------------------------- | :--------- | :-------------- | :-------- |
| 2   | - Read and understand **Amazon DynamoDB** architecture (Primary Key, Partition Key, Sort Key). |

[Image of Amazon DynamoDB architecture]
<br> - Learn concepts of Read/Write Capacity Units (RCU/WCU) and On-Demand mode. <br> - **Practice:** Create the first DynamoDB table, insert and query basic data. | 13/10/2025 | 13/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Deep dive into Index types: **Local Secondary Index (LSI)** and **Global Secondary Index (GSI)**. <br> - **Practice:** Create GSI for a DynamoDB table to support non-primary key queries. | 14/10/2025 | 14/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Learn about **Amazon ElastiCache** in-memory caching service (Redis and Memcached). <br> - Analyze the benefits of using a caching layer to offload RDS/DynamoDB. <br> - **Practice:** Launch an ElastiCache Cluster (e.g., Redis) in a Private Subnet. | 15/10/2025 | 15/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Learn how to **configure Security Group** for ElastiCache to ensure secure connections from EC2. <br> - Learn how applications connect and perform basic data operations on ElastiCache. <br> - **Practice:** Configure Security Group for the ElastiCache Cluster. | 16/10/2025 | 16/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Resource Cleanup & Review:** <br> - **Practice:** <br>&emsp; + Delete the created DynamoDB table. <br>&emsp; + Delete the ElastiCache Cluster. <br>&emsp; + Summarize pros/cons and Use-cases of RDS, DynamoDB, and ElastiCache. | 17/10/2025 | 17/10/2025 | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in Week 6:

- **DynamoDB Fundamentals:** Clearly understood the NoSQL model of DynamoDB, proficient in creating, managing tables and primary key types.
- **Query & Cost Optimization:** Grasped the role of **GSI/LSI** and capacity modes (On-Demand/Provisioned) in DynamoDB.
- **ElastiCache Fundamentals:** Understood the differences and benefits of Redis/Memcached. Grasped the role of caching in application architecture.

[Image of AWS ElastiCache architecture]

- **Caching Deployment:** Successfully launched an ElastiCache Cluster and set up network security via Security Group.
- **Service Differentiation:** Capable of comparing and selecting between RDS, DynamoDB, and ElastiCache for different data requirements.
