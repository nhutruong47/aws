---
title: "Week 11 Worklog"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Objectives for Week 11:

- Clearly understand the role of **AWS WAF** (Web Application Firewall) and **AWS Shield** in protecting applications from Layer 7 attacks (WAF) and DDoS (Shield).
- Master the operating mechanism and benefits of the intelligent threat detection service **Amazon GuardDuty**.
- Review and apply advanced security principles such as **IAM Policy Best Practices** and **Secrets Management**.
- Practice configuring basic security Rules.

### Tasks to be implemented this week:

| Day | Task                                                                                  | Start Date | Completion Date | Resources |
| :-- | :------------------------------------------------------------------------------------ | :--------- | :-------------- | :-------- |
| 2   | - Read and understand **AWS WAF** architecture and **Web ACL** (Access Control List). |

[Image of AWS Web ACL architecture]
<br> - Learn about Layer 7 attacks (SQL Injection, XSS) that WAF protects against. <br> - **Practice:** Create a Web ACL and learn about Managed Rule Groups. | 17/11/2025 | 17/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Learn about **AWS Shield Standard/Advanced** (DDoS Protection) and how it integrates with WAF/Route 53. <br> - **WAF Practice:** <br>&emsp; + Create a Rate-based Rule (limit access frequency). <br>&emsp; + Test blocking specific IPs (IP Set) via WAF. | 18/11/2025 | 18/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Learn about the threat detection service **Amazon GuardDuty** (using Machine Learning). <br> - **Practice:** Enable GuardDuty and review sample Findings (simulated threats) to understand how the service alerts. | 19/11/2025 | 19/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Review and apply **IAM Policy Best Practices** (Principle of Least Privilege). <br> - Learn about **AWS Secrets Manager** (credential rotation) and **AWS Systems Manager Parameter Store** (configuration storage). <br> - **Practice:** Review the IAM Policies created in Week 2. | 20/11/2025 | 20/11/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Summary & Resource Cleanup:** <br> - **Practice:** <br>&emsp; + Delete Web ACL/WAF Rules. <br>&emsp; + **Disable GuardDuty**. <br>&emsp; + Summarize security measures (Perimeter Security, Monitoring, Secrets Management) learned. | 21/11/2025 | 21/11/2025 | <https://cloudjourney.awsstudygroup.com/> |

### Results achieved in Week 11:

- **Perimeter Protection:** Clearly understood how WAF and Shield work at the network edge to protect resources like CloudFront, ALB.
- **Threat Detection:** Proficient in enabling and tracking alerts from **GuardDuty** to detect suspicious behavior within the AWS account.
- **Identity Management:** Reinforced knowledge of **IAM Policy** and understood the importance of Secrets Management using specialized services.
- **Security Construction:** Grasped how to integrate security services into application architecture (e.g., using WAF in front of ALB).
