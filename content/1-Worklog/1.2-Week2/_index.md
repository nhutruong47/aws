---
title: "Week 2 Worklog"
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Objectives for Week 2:

- Clearly understand the role and operation of the **EC2** (Elastic Compute Cloud) virtual server service.
- Master the process of launching, managing, and terminating an EC2 Instance.
- Master the concept and usage of **IAM Roles** to securely grant access permissions to EC2 resources.
- Use **AWS CLI** to perform basic EC2 management operations.

### Tasks to be implemented this week:

| Day | Task                                                                                                                                                                                                                                                                                            | Start Date | Completion Date | Resources                                 |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------- |
| 2   | - Read and understand the core components of **Amazon EC2** (AMI, Instance Type, Key Pair, Security Group). <br> - **Practice:** Launch the first EC2 Instance (select Free Tier type).                                                                                                         | 15/09/2025 | 15/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Learn about the secure permission mechanism **IAM Roles for EC2** (Instance Profiling). <br> - **Practice:** <br>&emsp; + Create IAM Policy allowing `s3:ListBucket`. <br>&emsp; + Create an IAM Role and attach this Policy. <br>&emsp; + Attach the newly created Role to the EC2 Instance. | 16/09/2025 | 16/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn **EC2 service management commands with AWS CLI**. <br> - **Practice:** <br>&emsp; + Use CLI to view EC2 Instance information (`describe-instances`). <br>&emsp; + Use CLI to Stop/Start Instance. <br>&emsp; + Manage Security Groups via CLI.                                          | 17/09/2025 | 17/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - **Integration Practice:** Verify IAM Role permissions. <br> - Log in via SSH/Session Manager to the EC2 Instance. <br> - **Practice:** Use the command `aws s3 ls` (CLI) from inside the EC2 to check if the Instance can read (list) S3 Buckets (proving the IAM Role is working).           | 18/09/2025 | 18/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Lifecycle & Cost Management:** <br> - Review EC2 lifecycle states (Pending, Running, Stopping, Terminated). <br> - **Practice:** <br>&emsp; + **Terminate** the EC2 Instance. <br>&emsp; + Delete the created IAM Role and Policy to clean up resources.                                    | 19/09/2025 | 19/09/2025      | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in Week 2:

- **EC2:** Grasped how to create, configure, and manage the lifecycle of EC2 virtual machines via Console and CLI. Understood the components that make up an EC2 instance.
- **IAM Roles:** Understood the advantages and usage of **IAM Role** (Instance Profile) to securely grant AWS service access permissions to EC2 resources, eliminating the need to store Access Keys on the server.
- **Advanced AWS CLI:** Learned how to use CLI commands to manage EC2 Instance states (Start, Stop, Describe) and perform remote operations.
- **Integration Practice:** Proved that the EC2 Instance can execute actions on S3 (e.g., `aws s3 ls`) thanks to permissions granted via IAM Role, confirming the security model works effectively.
- **Resource Cleanup:** Grasped the process of terminating EC2 Instances and cleaning up related IAM resources to ensure no costs are incurred.
