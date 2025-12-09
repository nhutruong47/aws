---
title: "Week 7 Worklog"
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Objectives for Week 7:

- Clearly understand the role and configuration of **EC2 Auto Scaling Group (ASG)** to automatically scale resources out and in.

[Image of AWS Auto Scaling architecture]

- Master the architecture and operation of **Elastic Load Balancer (ELB)** (especially ALB) to distribute traffic.
- Proficient in using **Amazon CloudWatch** to collect metrics, logs, create Dashboards, and set up Alarms.
- Practice setting up **Scaling Policies** based on monitoring metrics.

### Tasks to be implemented this week:

| Day | Task                                                                                                                                                                                                                               | Start Date | Completion Date | Resources                                 |
| :-- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------- |
| 2   | - Read and understand **Auto Scaling Group (ASG)** architecture, Launch Template. <br> - Learn about Load Balancer types (Classic, Application, Network). <br> - **Practice:** Create a Launch Template and configure a basic ASG. | 20/10/2025 | 20/10/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Deep dive into **Application Load Balancer (ALB)** and components (Listener, Target Group, Health Check).                                                                                                                        |

[Image of AWS Application Load Balancer components]
<br> - **Practice:** <br>&emsp; + Create ALB, Target Group. <br>&emsp; + Register ASG EC2 Instances into the Target Group. | 21/10/2025 | 21/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Learn about **Amazon CloudWatch** monitoring service (Metrics, Logs, Events). <br> - **Practice:** <br>&emsp; + View EC2, ALB, ASG Metrics on CloudWatch. <br>&emsp; + Create a CloudWatch Dashboard to track key metrics (CPU Utilization, Request Count). | 22/10/2025 | 22/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Learn about **CloudWatch Alarms** and **Scaling Policy** types (Target Tracking, Step Scaling). <br> - **Practice:** <br>&emsp; + Create CloudWatch Alarm based on CPU Utilization (e.g., > 80%). <br>&emsp; + Configure Scaling Policy for ASG using the created Alarm (scale out when CPU is high). | 23/10/2025 | 23/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Check & Resource Cleanup:** <br> - **Practice:** <br>&emsp; + Verify Scale Out/In process is working. <br>&emsp; + **Cleanup:** Delete CloudWatch Alarms, delete ASG (will automatically terminate EC2), delete ALB, delete Launch Template. | 24/10/2025 | 24/10/2025 | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in Week 7:

- **Scalability:** Successfully deployed application architecture capable of automatic scaling (Scale Out/In) via **ASG** and **Launch Template**.
- **Load Balancing:** Understood and configured **Application Load Balancer (ALB)** to distribute traffic and perform effective Health Checks.
- **Monitoring (Observability):** Mastered using **CloudWatch** to collect, visualize (Dashboard), and track resource health metrics.
- **Automation:** Successfully established performance-based auto-scaling mechanisms (Scaling Policy and CloudWatch Alarms).
- **Cost Management:** Mastered the process of cleaning up expensive resources like ALB and ASG.
