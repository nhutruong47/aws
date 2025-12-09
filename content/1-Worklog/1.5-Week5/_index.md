---
title: "Week 5 Worklog"
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Objectives for Week 5:

- Clearly understand the role and benefits of **Amazon RDS** service compared to self-managed databases on EC2.
- Master creating and connecting to a DB Instance (e.g., MySQL or PostgreSQL).
- Master key features: **Multi-AZ** (High Availability), **Read Replicas** (Read Scalability), and **Snapshot/Backup**.
- Practice managing network security for DB Instances via Security Groups.

### Tasks to be implemented this week:

| Day | Task                                                                                                                                                                                                                                                                                    | Start Date | Completion Date | Resources                                 |
| :-- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------- |
| 2   | - Read and understand the architecture of **Amazon RDS** (DB Instance, Engine, Master Username/Password, DB Security Group). <br> - Compare RDS with databases on EC2. <br> - **Practice:** Launch a DB Instance (select Free Tier) in a VPC created in Week 3 (select Private Subnet). | 06/10/2025 | 06/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Learn about connection and network security for RDS. <br> - **Practice:** <br>&emsp; + Configure **Security Group** for RDS to only allow access from **EC2 Instance Security Group** (created in Week 2). <br>&emsp; + Use a Client tool or EC2 to connect and create a basic table. | 07/10/2025 | 07/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn about **Multi-AZ Deployment** feature to ensure High Availability (HA).                                                                                                                                                                                                         |

[Image of AWS RDS Multi-AZ architecture]
<br> - Learn about **Automated Backups** and **DB Snapshots** (Manual backup). <br> - **Practice:** Enable Multi-AZ for the Instance and create a manual DB Snapshot. | 08/10/2025 | 08/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Learn about **Read Replicas** to offload the DB Master. <br> - **Practice:** <br>&emsp; + Create a Read Replica for the primary DB Instance. <br>&emsp; + Simulate application connection to Read Replica to scale read capacity. <br>&emsp; + Learn about promoting Read Replica to Standalone DB. | 09/10/2025 | 09/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Cleanup and Optimization:** <br> - **Practice:** <br>&emsp; + Delete Read Replica. <br>&emsp; + Delete primary DB Instance (Note: Uncheck create Final Snapshot if not needed). <br>&emsp; + Clean up all related Snapshots and Security Groups. | 10/10/2025 | 10/10/2025 | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in Week 5:

- **RDS Management:** Clearly understood the benefits of RDS and proficient in creating, configuring, and connecting to DB Instances.
- **Connection Security:** Mastered using Security Groups to only allow specific resources (like EC2) to access the database, ensuring network layer security.
- **High Availability (HA):** Understood and successfully practiced deploying **Multi-AZ** to protect the database from Availability Zone (AZ) failures.
- **Scalability:** Understood and practiced creating **Read Replicas** to optimize read performance and offload the DB Master.
- **Backup & Recovery:** Grasped the process of creating **DB Snapshots** and how RDS performs **Automated Backups**.
