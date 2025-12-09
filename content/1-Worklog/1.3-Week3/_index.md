---
title: "Week 3 Worklog"
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Objectives for Week 3:

- Clearly understand the role and core components of the **Amazon Virtual Private Cloud (VPC)** virtual network service.

[Image of AWS VPC architecture diagram]

- Master the creation and configuration of VPC, Subnets (Public/Private), Internet Gateway (IGW), and Route Tables.
- Master the two-layer security mechanism: **Security Group (SG)** and **Network Access Control List (NACL)**.
- Practice deploying an EC2 Instance into a custom VPC.

### Tasks to be implemented this week:

| Day | Task                                                                                                                                                                                                                                                                                                                                                             | Start Date | Completion Date | Resources                                 |
| :-- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------- |
| 2   | - Read and understand **VPC** architecture: Concepts of IP, CIDR Block, Subnet, Availability Zone (AZ). <br> - **Practice:** Create a new VPC with a custom CIDR range (e.g., `10.0.0.0/16`). <br> - Create two Subnets: one Public and one Private.                                                                                                             | 22/09/2025 | 22/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Learn about **Internet Gateway (IGW)**, **Route Table**, and their roles in providing Internet access. <br> - **Practice:** <br>&emsp; + Create and attach IGW to the VPC. <br>&emsp; + Configure **Public Route Table** to route traffic to IGW. <br>&emsp; + Associate the Public Route Table with the Public Subnet.                                        | 23/09/2025 | 23/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Learn about the **Security Group (SG)** security mechanism (Stateful) and its operating principles. <br> - **Practice:** <br>&emsp; + Launch an EC2 Instance in the Public Subnet. <br>&emsp; + Configure SG to only allow SSH/RDP (Port 22/3389) from personal IP. <br>&emsp; + Attempt access to verify SG security features.                                | 24/09/2025 | 24/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Learn about the **Network Access Control List (NACL)** security mechanism (Stateless). <br> - **Practice:** <br>&emsp; + Configure NACL for the Public Subnet (test creating Deny rules). <br>&emsp; + Detailed differentiation between SG and NACL when handling inbound/outbound traffic. <br>&emsp; + Learn the concept of NAT Gateway (in Private Subnet). | 25/09/2025 | 25/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Cleanup & General Review:** <br> - **Practice:** <br>&emsp; + Terminate the EC2 Instance. <br>&emsp; + **Delete all VPC components** created in the correct order (Detach IGW -> Delete Subnets -> Delete Route Tables -> Delete VPC) to clean up costs. <br>&emsp; + Summarize the VPC components learned.                                                  | 26/09/2025 | 26/09/2025      | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in Week 3:

- **VPC Configuration:** Understood and manually created VPC, Subnets (Public/Private), Internet Gateway, and Route Tables to route traffic.
- **Network Security:** Mastered and distinguished the two-layer security mechanism: **Security Group** (Stateful, operates at the Instance level) and **NACL** (Stateless, operates at the Subnet level).
- **Basic Deployment:** Successfully deployed an EC2 Instance in a self-created VPC and verified Internet connectivity.
- **Cleanup Skills:** Successfully performed network resource cleanup in the correct order (ensuring no unnecessary resources are left behind), contributing to effective cost management.
