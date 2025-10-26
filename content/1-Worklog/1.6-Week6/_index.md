---
title: "Week 6 Worklog"
date: "2025-09-11"
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---
### Week 6 Objectives:

* Complete AWS Security and Cost Management course on DataCamp
* Understand the AWS Shared Responsibility Model and why cloud security is critical
* Learn about governance, compliance, and regulatory requirements
* Explore AWS security and compliance automation tools (Security Hub, Trusted Advisor, GuardDuty)
* Apply the principle of least privilege to IAM users, groups, and roles
* Secure networks using VPC, NACLs, security groups, and AWS WAF
* Implement compute and data security with encryption, Security Groups, and credential management

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 1   | - Complete Chapter 1: Foundation Security & Governance <br>&emsp; + AWS Shared Responsibility Model <br>&emsp; + Why cloud security is important <br>&emsp; + Customer vs AWS responsibilities | 13/10/2025 | 13/10/2025      | DataCamp - AWS Security Course |
| 2   | - Complete Chapter 1 continued: <br>&emsp; + Compliance and governance <br>&emsp; + Regulations (Sarbanes-Oxley, GDPR) <br>&emsp; + Governance functions (identify, detect, protect, respond, recover) | 13/10/2025 | 13/10/2025      | DataCamp - AWS Security Course |
| 3   | - Complete Chapter 1 continued: <br>&emsp; + AWS Security Hub overview <br>&emsp; + AWS Trusted Advisor <br>&emsp; + GuardDuty threat detection <br>&emsp; + Security automation tools comparison | 14/10/2025 | 14/10/2025      | DataCamp - AWS Security Course |
| 4   | - Complete Chapter 2: Identity and Access Management <br>&emsp; + Principle of least privilege (5-step approach) <br>&emsp; + Root user security, MFA <br>&emsp; + User and group security <br>&emsp; + Credential management (Secrets Manager) | 14/10/2025 | 14/10/2025      | DataCamp - AWS Security Course |
| 5   | - Complete Chapter 2 continued: <br>&emsp; + IAM users vs roles (who, what, where) <br>&emsp; + Policies and permissions <br>&emsp; + IAM Identity Center <br>&emsp; + Assign roles to computing resources | 15/10/2025 | 15/10/2025      | DataCamp - AWS Security Course |
| 6   | - Complete Chapter 3: Network Security <br>&emsp; + Networking basics (subnets, networks, routers) <br>&emsp; + Virtual Private Cloud (VPC) <br>&emsp; + VPC security (5 steps) <br>&emsp; + NACL vs Security Group vs AWS WAF | 15/10/2025 | 15/10/2025      | DataCamp - AWS Security Course |
| 7   | - Complete Chapter 3 continued: <br>&emsp; + AWS Marketplace for security solutions <br>&emsp; + AWS Firewall Manager <br>&emsp; + VPC flow logs | 16/10/2025 | 16/10/2025      | DataCamp - AWS Security Course |
| 8   | - Complete Chapter 4: Compute and Data Security <br>&emsp; + EC2 security (SSH keys, patches, security groups) <br>&emsp; + Security Groups vs NACLs <br>&emsp; + Data at-rest encryption (S3, EBS) <br>&emsp; + S3 public access protection | 16/10/2025 | 16/10/2025      | DataCamp - AWS Security Course |
| 9   | - Complete Chapter 4 continued & Cost Optimization: <br>&emsp; + AWS KMS for encryption key management <br>&emsp; + Glacier for archival storage <br>&emsp; + Disaster recovery (versioning, replication) <br>&emsp; + Trusted Advisor cost optimization recommendations | 17/10/2025 | 17/10/2025      | DataCamp - AWS Security Course |
| 10  | - Hands-on practice with AWS Sandbox: <br>&emsp; + Enable Security Hub and review findings <br>&emsp; + Configure IAM users and groups with least privilege <br>&emsp; + Create and attach IAM roles to EC2 instances <br>&emsp; + Review Trusted Advisor recommendations | 18/10/2025 | 18/10/2025      | AWS Sandbox Account |


### Week 6 Achievements:

* Understanding why cloud security is critical:
  * Data breaches cause loss of customer trust, license revocation in regulated industries, and financial consequences
  * Between 2018-2022, FBI received cybercrime complaints totaling $27.6 billion in losses in the US
  * Large companies store sensitive customer data (financial, health data) requiring appropriate security controls

* AWS Shared Responsibility Model and governance:
  * Cloud security is shared between AWS and customers (similar to tenant-landlord relationship)
  * AWS responsibilities: physical security of data centers, equipment, networking, power backup, infrastructure software, redundancy
  * Customer responsibilities for infrastructure services: operating systems, application security, data encryption, access controls, server updates
  * Responsibilities change with service type: serverless services (Lambda, Glue) shift more responsibility to AWS
  * Cloud governance framework includes: Identify critical resources, Detect anomalies, Protect critical resources, Incident response planning, Recovery processes

* AWS compliance and regulations:
  * Governance ensures corporate strategy, ethical behavior, risk management, and compliance
  * Regulations worldwide: Sarbanes-Oxley (US public companies), GDPR (Europe consumer data protection)
  * Security Hub: automatically checks AWS resources for security best practices, finds misconfiguration, standard format findings
  * AWS Shield: protects from DDoS attacks
  * CloudWatch: enables automated continuous monitoring for anomalies and malicious activities

* AWS security and compliance automation tools:
  * Security Hub: centralized security posture dashboard, aggregates alerts from 60+ AWS security services, supports remediation via Lambda
  * Trusted Advisor: monitors best practices for cost optimization, system performance, reliability, and security gaps
  * GuardDuty: threat detection service monitoring for malicious activity (works independently, doesn't affect resource performance)
  * Inspector: automated vulnerability management, continuously scans AWS workloads for software vulnerabilities
  * CloudTrail: enables auditing, security monitoring, and operational troubleshooting by tracking user activity and API usage

* Principle of least privilege implementation:
  * Core principle: grant users and systems the narrowest set of privileges to complete required tasks
  * Five-step strategy: 
    1. Begin with coarse-grained security controls (block public access at Organization level)
    2. Apply fine-grained controls for specific access needs
    3. Use accounts as boundaries for security administration
    4. Prioritize short-term credentials via AWS Security Token Service (STS)
    5. Enforce broad invariants (e.g., regional restrictions for business operations)
  * Balancing act: prevent dangerous actions while enabling innovation and speed

* Account security framework:
  * Root user security: strong password, multi-factor authentication, avoid creating access keys, use group email, multi-person approval
  * Users & groups: enable MFA for all IAM users, use groups for consistent permissions, rotate passwords and access keys regularly
  * Computing resources: use IAM roles for virtual machines, Systems Manager for configuration and patch management
  * Credential security: use AWS Secrets Manager for database credentials and API keys with automatic rotation, integrate with other AWS services

* Identity and Access Management (IAM) fundamentals:
  * Who: Principals (users with long-term credentials OR roles with short-term credentials via STS)
  * What: Policies (text documents specifying authorized principals and resources)
  * Where: AWS Organizations (organizational units like production, development, test)
  * IAM Identity Center: creates or connects workforce users, centrally manages access to multiple AWS accounts
  * Single sign-on support for Office 365 and other work accounts

* Network security in AWS:
  * Networking basics: subnets (connected computers), networks (connected subnets), routers (route traffic), route tables (address mapping)
  * Virtual Private Cloud (VPC): virtual network with subnets, route tables, firewall, DNS
  * Five steps to secure VPCs: appropriate subnet type, isolate environments, create NACLs, create firewall/AWS WAF, create VPC flow logs
  * NACL vs Security Group vs AWS WAF comparison: NACL (stateless, subnet-level, free), Security Groups (stateful, instance-level, free), WAF (stateful, application-level, paid)
  * AWS Marketplace: find, buy, deploy third-party security software (e.g., Cisco, Juniper Networks)

* Compute and data security:
  * Securing data in-transit (network) and data at-rest (hard disks)
  * EC2 security: use SSH keys instead of passwords, update OS with latest patches, control traffic with security groups, assign IAM roles to eliminate credential storage
  * Security Groups: virtual firewall for EC2 instances, stateful (remember connection status), allow outbound by default
  * Security Groups vs NACLs: Security Groups allow fine-grained traffic to individual servers, are stateful, and allow outbound by default; NACLs apply to entire subnets and are stateless
  * Data at-rest encryption: use AWS Key Management Service (KMS), supports S3 and EBS
  * S3 security: disable public access, use versioning, Glacier for archival storage, replication for disaster recovery
  * Glacier: archival storage built on S3, optimized for large volume and infrequent/slower retrieval time
  * AWS Knowledge Center: answers to frequent customer questions
  * Security blog: deep-dives into best practices, new features, how-to guides

* Practiced hands-on with AWS Sandbox:
  * Enabled Security Hub and reviewed security findings
  * Created IAM users and groups with least privilege permissions
  * Created and attached IAM roles to EC2 instances
  * Reviewed Trusted Advisor recommendations for cost optimization

### Summary / Notes

This week completed the comprehensive AWS Security and Cost Management course on DataCamp. The course provided a thorough understanding of cloud security fundamentals, governance, and best practices:

**Key Takeaways:**

1. **Cloud Security is Critical**: Data breaches can cause loss of customer trust, license revocation, and financial losses. The FBI reported cybercrime-related losses of $27.6 billion between 2018-2022 in the US alone.

2. **Shared Responsibility Model**: Security is a shared responsibility. AWS manages hardware, infrastructure, and data centers ("Security OF the cloud"). Customers manage operating systems, applications, data encryption, and access controls ("Security IN the cloud"). The division is like a tenant-landlord relationship.

3. **Governance Framework**: Cloud governance ensures corporate strategy, ethical behavior, risk management, and compliance. Five functions: Identify, Detect, Protect, Respond, and Recover. Important regulations include Sarbanes-Oxley (US) and GDPR (Europe).

4. **Security Automation Tools**: AWS offers many specialized tools. Security Hub provides a centralized dashboard aggregating alerts from 60+ services. Trusted Advisor monitors cost, performance, and security. GuardDuty detects threats. Inspector scans for vulnerabilities. CloudTrail tracks user activity for auditing.

5. **Principle of Least Privilege**: Grant the narrowest set of privileges needed for tasks. Five-step approach: coarse-grained controls, fine-grained exceptions, account boundaries, short-lived credentials (STS), and enforce invariants.

6. **Account Security**: Protect root user with MFA and strong passwords. Enable MFA for all IAM users. Use groups for permissions. Prefer roles over long-term credentials for compute resources. Use Secrets Manager for secure credential management.

7. **Network Security**: Understand VPC components (subnets, route tables, firewalls, DNS). Implement VPC security through appropriate subnet types, environment isolation, NACLs, firewalls/WAF, and flow logs. Compare NACLs (stateless, subnet-level, free) vs Security Groups (stateful, instance-level, free) vs WAF (application-level, paid).

8. **Compute and Data Security**: Secure EC2 with SSH keys, OS patches, and Security Groups. Use encryption at-rest with KMS for keys. Protect S3 buckets by disabling public access. Implement disaster recovery with versioning, Glacier for archiving, and replication.

**Practical Application**: 
Practiced with AWS Sandbox account to enable Security Hub, configure IAM with least privilege, attach roles to EC2 instances, and review Trusted Advisor recommendations for cost optimization (identifying idle load balancers and underutilized resources).

**Course Instructor**: Dev Bhosale (Cloud & Data Professional, DataCamp Instructor)

References:
- DataCamp: AWS Security and Cost Management course
- AWS Security Hub Documentation
- AWS Trusted Advisor Documentation
- AWS IAM Documentation
- AWS VPC Documentation
