---
title: "Event 5: AWS Cloud Mastery Series #3 - According to AWS Well-Architected Security Pillar"
date: 2025-09-09
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

# Summary Report: “AWS Cloud Mastery Series #3: According to AWS Well-Architected Security Pillar”

### Date and Topic

- **Date and Time:** Saturday, November 29, 2025 (8:30 AM – 12:00 PM)
- **Topic:** According to AWS Well-Architected Security Pillar

### Event Objectives

- To focus on the **Security Pillar** of the AWS Well-Architected Framework.
- To provide deep knowledge about 5 key security domains: **Identity & Access Management (IAM), Detection, Infrastructure Protection, Data Protection, and Incident Response**.
- To introduce best practices and services for protecting workloads on the Cloud.

### Speakers

- Detailed speaker information is not available in the original data, assumed to be AWS Vietnam Solution Architects/Specialists.

### Highlights

#### 1. Security Foundation & IAM (Identity & Access Management)

- **Core Principles:** **Least Privilege, Zero Trust, Defense in Depth**, and the **Shared Responsibility Model**.
- **Modern IAM:** Managing Users, Roles, and Policies, avoiding long-term credentials, and utilizing **IAM Identity Center** (SSO), **MFA**, and **Access Analyzer**.

#### 2. Detection & Infrastructure Protection

- **Detection & Monitoring:** Using **CloudTrail** (org-level), **GuardDuty** (threat detection), **Security Hub**, and logging (VPC Flow Logs).
- **Network Security:** VPC segmentation, distinguishing **Security Groups vs NACLs**, and utilizing **WAF + Shield** and **Network Firewall**.

#### 3. Data Protection & Incident Response

- **Data Protection:** Key management and encryption using **KMS** (Key Management Service) for data at-rest and in-transit (S3, RDS). Utilizing **Secrets Manager** to store and rotate secrets.
- **Incident Response (IR):** The IR lifecycle process and **Playbooks** for responding to scenarios like compromised IAM keys or S3 public exposure, utilizing **Lambda/Step Functions** for automation.

### Key Takeaways

#### Comprehensive Security Knowledge

- **5 Security Pillars:** Gained a complete understanding of the comprehensive security structure on the Cloud, from identity protection to incident response.
- **Modern IAM:** Understood how to design IAM architecture that avoids long-term credentials to mitigate risk.
- **Data Protection:** Mastered the essential standards for encryption and key management for sensitive data.
- **IR Automation:** Understood the role of automation in rapidly responding to security incidents (Auto-response).

### Application to Work

- **Security Audit:** Applying the principles of the Security Pillar to audit and improve the current security configurations of ongoing projects.
- **GuardDuty & Security Hub Setup:** Deploying these AWS services in the account to establish a continuous threat detection mechanism.
- **Secrets Management:** Using AWS Secrets Manager and Parameter Store to store sensitive information instead of hardcoding, and establishing rotation mechanisms.

### Event Experience

- **Importance of Security:** The event emphasized that security is a shared responsibility and must be integrated from the design phase (security by design).
- **Learning Through Practice:** The Mini Demos on validating IAM Policies and incident response were highly practical, demonstrating how AWS tools function.
- **Mindset Shift:** Helped transition from a "blocking" mindset to a "detection and automated response" mindset.

> This event is mandatory for me to build any application on AWS securely and adhere to the highest standards.

![Event image](/images/even1.1.jpg)
![Event image](/images/even2.1.jpg)
![Event image](/images/dsf.jpg)
![Event image](/images/dg.jpg)
