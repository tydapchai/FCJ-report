---
title: "Event 5"
date: "2025-11-29"
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---
# Summary Report: "AWS Well-Architected Security Pillar Workshop – AWS Cloud Mastery Series #3"

## Event Overview

| | |
|---|---|
| **Event Name** | AWS Well-Architected Security Pillar Workshop – AWS Cloud Mastery Series #3 |
| **Date** | November 29, 2025 |
| **Role** | Attendee |
| **Format** | On-site workshop |
| **Duration** | Full-day workshop (9:15 AM – 11:50 AM+) |
| **Location** | 26th floor, Bitexco Financial Tower, District 1, Ho Chi Minh City, Vietnam |

This comprehensive workshop focused exclusively on the Security pillar of the AWS Well-Architected Framework. The event provided deep technical coverage of security best practices, tools, and patterns for building secure workloads on AWS. Each session built upon previous concepts, creating a complete picture of AWS security.

---

## Workshop Agenda

### Session 1: Identity & Access Management (9:15 – 9:45 AM)
**Speakers:** Huynh Hoang Long, Dinh Le Hoang Anh

#### IAM Fundamentals

**What is IAM?:** Understanding Identity and Access Management

**What IAM Manages:**
- **Users:** Individual accounts for people and applications
- **Groups:** Collections of users with shared permissions
- **Roles:** Temporary credentials for services and users
- **Policies:** Documents that define permissions

**What IAM Ensures:**
- **Authentication:** Verifying identity
- **Authorization:** Controlling access to resources
- **Auditability:** Tracking who did what and when

#### IAM Best Practices

**Principle of Least Privilege**
- Granting only the minimum permissions necessary
- Starting with no permissions and adding only what's needed
- Regular review and removal of unnecessary permissions
- Using IAM Access Analyzer to identify over-permissive policies

**Root Account Security**
- **Never use root access keys:** Root credentials provide unlimited access
- **Delete root access keys:** Removing any existing root access keys
- **Enable MFA for root:** Multi-factor authentication as an additional security layer
- **Use root only for account management:** Limiting root usage to essential tasks

**Policy Management**
- Use managed policies: Leveraging AWS-managed policies when possible
- Create custom policies: When AWS-managed policies don't fit
- Avoid wildcards ("*"): Being specific about allowed actions and resources
- Policy versioning: Managing policy changes over time
- Policy testing: Using IAM policy simulator

**Role-Based Access**
- Use roles instead of users for applications: Roles provide temporary credentials
- Assume roles: Using role assumption for cross-account and service access
- Role chaining: Understanding role assumption limits
- Session duration: Setting appropriate session timeouts

**AWS Login Best Practices**
- Use AWS SSO or IAM Identity Center: Centralized identity management
- Avoid long-lived access keys: Preferring temporary credentials
- Rotate credentials regularly: Changing access keys periodically
- Use AWS CLI with profiles: Managing multiple credentials securely

**Multi-Factor Authentication (MFA)**
- MFA for all users: Requiring MFA for human users
- TOTP (Time-based One-Time Password): Using authenticator apps
- FIDO2: Hardware security keys for stronger authentication
- MFA for root: Critical for root account protection
- MFA for privileged operations: Requiring MFA for sensitive actions

**Credential Rotation**
- Regular rotation: Changing credentials on a schedule
- AWS Secrets Manager: Automated rotation for database credentials, API keys, etc.
- Rotation strategies: Different approaches for different credential types
- Monitoring rotation: Ensuring rotation occurs successfully

#### Single Sign-On (SSO) / IAM Identity Center

**SSO Concepts**
- Single sign-on: Logging in once to access multiple services
- Centralized identity management: One place to manage all identities
- Multi-account integration: Using SSO across AWS Organizations
- Multiple roles: Users can have different roles for different accounts

**IAM Identity Center Features**
- User and group management: Centralized user administration
- Application assignments: Assigning access to AWS and third-party applications
- Permission sets: Reusable collections of permissions
- Session management: Controlling session duration and policies

**AWS Organizations Integration**
- Organization-wide SSO: SSO works across all accounts in an organization
- Account management: Simplifying access to multiple accounts
- Centralized governance: Managing access from one place

#### Service Control Policies (SCPs)

**SCP Overview**
- Maximum permissions: Setting the maximum permissions for accounts in an organization
- Not granting permissions: SCPs filter permissions but don't grant them
- Deny by default: Understanding how SCPs work with allow/deny logic
- Organization-level control: Applying policies at the organization level

**SCP Use Cases**
- Preventing certain actions: Blocking risky operations across all accounts
- Enforcing compliance: Ensuring all accounts meet compliance requirements
- Cost control: Preventing expensive operations
- Security guardrails: Enforcing security policies organization-wide

#### Permission Boundaries

**Permission Boundary Concepts**
- Maximum permissions for policies: Setting limits on what policies can grant
- Applied to roles or users: Using permission boundaries to constrain access
- Not granting permissions: Like SCPs, they filter rather than grant
- Fine-grained control: More granular than SCPs

**Use Cases**
- Delegating policy creation: Allowing teams to create policies within limits
- Preventing privilege escalation: Ensuring users can't grant themselves more access
- Compliance: Meeting regulatory requirements for access control

#### Relationship Between IAM, SCPs, and Permission Boundaries
- **IAM Policies:** Grant permissions to users, groups, and roles
- **Permission Boundaries:** Limit what IAM policies can grant
- **SCPs:** Limit what's possible at the organization level
- **Evaluation order:** Understanding how these work together
- **Effective permissions:** Calculating what a user can actually do

#### Credentials Spectrum

**Long-term Credentials**
- IAM user access keys: Permanent credentials with no expiration
- Risks: If compromised, remain valid until manually rotated
- Use cases: Limited scenarios where long-term credentials are necessary
- Best practice: Avoid when possible

**Short-term Credentials**
- AWS Security Token Service (STS): Temporary credentials
- Benefits: Automatic expiration, reduced risk if compromised
- Session tokens: Time-limited access
- Best practice: Use short-term credentials whenever possible

#### IAM Access Analyzer
- Security vulnerability detection: Identifying security issues based on logic
- External access analysis: Finding resources accessible from outside your account
- Policy analysis: Identifying over-permissive policies
- Continuous monitoring: Ongoing analysis of your IAM configuration

---

### Session 2: Detection & Continuous Monitoring (9:50 – 10:20 AM)
**Speakers:** Tran Duc Anh, Nguyen Tuan Thinh, Nguyen Do Thanh Dat

#### AWS CloudTrail

**Multi-layer Security Visibility**
- API call logging: Recording all API calls made in your AWS account
- Who, what, when, where: Comprehensive audit trail
- Management events: Administrative actions
- Data events: Resource-level operations (S3 object access, Lambda invocation)
- CloudTrail logs: Stored in S3 with integrity validation

**Alerting & Automation with EventBridge**
- EventBridge integration: Automatically responding to CloudTrail events
- Rule creation: Defining patterns to match
- Target actions: Triggering responses (Lambda, SNS, etc.)
- Real-time monitoring: Immediate notification of security events
- Automated remediation: Automatically fixing issues

**Detection as Code**
- Infrastructure as Code for monitoring: Defining detection rules in code
- Version control: Tracking changes to detection logic
- Reproducibility: Consistent detection across environments
- Testing: Validating detection rules before deployment

#### Amazon GuardDuty

**Business Pain Points**
- Threat detection: Identifying malicious activity and unauthorized behavior
- Scale: Monitoring vast amounts of data
- Expertise: Requiring security expertise to identify threats
- False positives: Reducing noise from legitimate activities

**GuardDuty Overview**
- Managed threat detection: Continuous monitoring for malicious activity
- Machine learning: Using ML to identify threats
- Threat intelligence: Leveraging AWS and third-party threat feeds
- No infrastructure management: Fully managed service

**Data Sources**
- VPC Flow Logs: Network traffic analysis
- CloudTrail event logs: API call analysis
- DNS logs: Domain name resolution analysis
- Malware protection: EKS runtime protection
- S3 protection: Object-level threat detection

**What GuardDuty Monitors**
- Unauthorized API calls: Suspicious API activity
- Compromised instances: EC2 instances communicating with malicious IPs
- Account compromise: Unusual account activity
- Instance compromise: Malware and suspicious behavior
- Container threats: EKS cluster security issues

**Advanced Protection Plans**
- S3 Protection: Monitoring S3 data events for threats
- Kubernetes Protection: EKS runtime threat detection
- Malware Protection: Scanning EC2 and ECS workloads
- RDS Protection: Database threat detection
- Lambda Protection: Serverless function monitoring

**GuardDuty Agent**
- On-premises protection: Extending GuardDuty to on-premises environments
- Agent deployment: Installing agents on servers
- Threat detection: Monitoring on-premises workloads
- Unified view: Single pane of glass for cloud and on-premises

**GuardDuty Alerting & Automation with EventBridge**
- Finding notifications: Alerting on security findings
- Severity levels: Critical, high, medium, low
- Automated responses: Triggering remediation workflows
- Integration: Working with other AWS services

**GuardDuty Detection as Code**
- Code-based detection rules: Defining custom detection logic
- Suppression rules: Filtering false positives
- Version control: Managing detection rules in Git
- Testing: Validating detection rules

#### AWS Security Hub

**CSPM (Cloud Security Posture Management)**
- Security posture assessment: Evaluating overall security posture
- Compliance checking: Verifying compliance with standards
- Resource inventory: Understanding what you have
- Risk assessment: Identifying security risks

**Centralized Alerting & Normalization**
- ASFF (AWS Security Finding Format): Standardized finding format
- Aggregation: Collecting findings from multiple sources
- Normalization: Converting findings to common format
- Deduplication: Removing duplicate findings
- Prioritization: Ranking findings by severity

**Security Hub Features**
- Automated security checks: Continuous compliance monitoring
- Security insights: Understanding security trends
- Custom insights: Creating custom analysis
- Integration: Working with partner security tools
- Remediation: Automated and manual remediation options

**Compliance Standards**
- AWS Foundational Security Best Practices: AWS-recommended security practices
- CIS AWS Foundations Benchmark: Industry-standard security controls
- PCI DSS: Payment card industry compliance
- Custom frameworks: Defining your own compliance standards

**Detection as Code**
- Code-based compliance: Defining compliance rules in code
- Custom insights: Creating custom security analysis
- Automation: Automating compliance checking
- Reporting: Generating compliance reports

---

### Session 3: Network & Workload Security (10:30 – 11:10 AM)
**Speaker:** Nguyen Van Hoang Kha

#### Network Security Fundamentals

**Good Traffic Flow**
- Understanding normal traffic patterns: Baseline for detecting anomalies
- East-west traffic: Traffic within the network
- North-south traffic: Traffic entering/leaving the network
- Traffic segmentation: Isolating different types of traffic

**Network Attack Vectors**
- DDoS attacks: Distributed denial of service
- Man-in-the-middle: Intercepting communications
- Port scanning: Probing for open ports
- DNS attacks: DNS spoofing and hijacking
- Data exfiltration: Unauthorized data removal

**Anatomy of an Exploit - Melofee**
- Case study: Real-world attack analysis
- Attack progression: How attacks unfold
- Vulnerability exploitation: Understanding exploit techniques
- Defense strategies: How to prevent similar attacks

**Network Protection Use Cases**
- Inbound protection: Protecting against external threats
- Outbound protection: Preventing data exfiltration
- East-west protection: Securing internal traffic
- Combined protection: Layered security approach

#### AWS Layered Security

**AWS Firewall Manager**
- Centralized firewall management: Managing firewalls across accounts
- Policy enforcement: Ensuring consistent security policies
- Compliance: Meeting security requirements organization-wide

**AWS Network Firewall**
- Managed network firewall: Stateful inspection firewall
- Traffic filtering: Controlling network traffic
- Intrusion prevention: Detecting and blocking threats
- Integration: Working with VPCs and Transit Gateway

**DNS Firewall**
- Route 53 Resolver DNS Firewall: Filtering DNS queries
- Domain filtering: Blocking malicious domains
- Threat intelligence: Using threat feeds
- Logging: Tracking DNS queries

**AWS WAF**
- Web Application Firewall: Protecting web applications
- Rule-based filtering: Custom and managed rules
- Rate limiting: Preventing abuse
- Bot protection: Blocking malicious bots

**VPC Flow Logs**
- Network traffic logging: Recording network flows
- Traffic analysis: Understanding network behavior
- Security monitoring: Detecting suspicious traffic
- Troubleshooting: Diagnosing network issues

**Traffic Mirroring**
- Copying network traffic: For analysis and monitoring
- Security tools: Feeding traffic to security appliances
- Compliance: Meeting monitoring requirements

#### VPC Security Groups

**Security Group Basics**
- Instance-level firewall: Controlling traffic to EC2 instances
- Stateful firewall: Automatically allowing return traffic
- Default deny: Only explicitly allowed traffic is permitted
- Allow rules only: Cannot create explicit deny rules

**Security Group Best Practices**
- Least privilege: Only allowing necessary traffic
- Specific ports and protocols: Being precise about allowed traffic
- Source restrictions: Limiting source IPs when possible
- Regular review: Auditing security group rules

**VPC Peering & Transit Gateway**
- VPC peering: Connecting VPCs securely
- Transit Gateway: Centralized network hub
- Route management: Controlling traffic routing
- Security considerations: Securing inter-VPC traffic

**Security Group Sharing**
- Cross-account sharing: Sharing security groups across accounts
- Use cases: Centralized security group management
- Best practices: When and how to share security groups

**Security Group Referencing**
- Referencing other security groups: Allowing traffic from specific security groups
- Dynamic rules: Rules that adapt to group membership
- Use cases: Simplifying security group management

#### Network ACLs (NACLs)

**NACL Basics**
- Subnet-level firewall: Controlling traffic at subnet level
- Stateless: Must explicitly allow return traffic
- Allow and deny rules: Can create both allow and deny rules
- Rule evaluation: Rules evaluated in order

**NACL vs Security Groups**
- When to use NACLs: Subnet-level controls
- When to use Security Groups: Instance-level controls
- Combined use: Using both for defense in depth

**Security Groups & NACLs Against Attack Vectors**
- DDoS protection: Rate limiting and filtering
- Port scanning: Blocking unnecessary ports
- Data exfiltration: Monitoring and blocking outbound traffic
- Layered defense: Multiple layers of protection

#### Route 53 VPC DNS Resolver

**DNS Resolution**
- Private DNS: Resolving DNS queries within VPC
- DNS filtering: Blocking malicious domains
- DNS logging: Tracking DNS queries
- Hybrid DNS: Resolving on-premises and cloud resources

#### Route 53 DNS Firewall Features

**DNS Firewall Capabilities**
- Domain filtering: Blocking access to malicious domains
- Threat intelligence: Using AWS and custom threat lists
- Custom rules: Creating domain allow/deny lists
- Logging: Recording DNS queries for analysis

**SG, NACL, DNS Firewall Against Attack Vectors**
- Comprehensive protection: Multiple layers of network security
- Attack prevention: Blocking attacks before they reach resources
- Visibility: Understanding network traffic patterns

#### Inter-VPC and On-Premises via Transit Gateway

**Transit Gateway**
- Centralized connectivity: Hub for VPC and on-premises connectivity
- Route management: Controlling traffic routing
- Security: Applying security policies at transit gateway
- Scalability: Supporting large-scale networks

#### AWS Network Firewall

**Firewall Behavior**
- Stateful inspection: Understanding connection state
- Traffic filtering: Allowing or denying traffic based on rules
- Intrusion prevention: Detecting and blocking threats
- SSL/TLS inspection: Decrypting and inspecting encrypted traffic

**Network Firewall Rules**
- Stateless rules: Simple allow/deny based on header fields
- Stateful rules: Understanding connection context
- Rule groups: Organizing and reusing rules
- Suricata rules: Using Suricata-compatible rules

**Multiple VPC Endpoints**
- VPC endpoint integration: Working with VPC endpoints
- Traffic inspection: Inspecting traffic to AWS services
- Security: Ensuring secure access to AWS services

**Automated Domain Lists**
- Threat intelligence feeds: Automatically updating threat lists
- Custom lists: Adding your own domain lists
- Maintenance: Reducing manual list management

**Native Transit Gateway Integration**
- Seamless integration: Working directly with Transit Gateway
- Route propagation: Automatic route management
- Scalability: Handling large-scale deployments

**Multi-layer Security Against Attack Vectors**
- Defense in depth: Multiple security layers
- Comprehensive protection: Covering all attack vectors
- Visibility: Understanding threats across layers

---

### Session 4: AWS Data Protection (11:15 – 11:45 AM)
**Speakers:** Thinh Lam, Viet Nguyen

#### AWS Key Management Service (KMS)

**KMS Workflow**
- Key creation: Creating and managing encryption keys
- Key usage: Using keys to encrypt and decrypt data
- Key rotation: Automatically rotating keys
- Access control: Controlling who can use keys

**KMS Policies**
- Key policies: Defining who can use keys
- IAM policies: Additional access control
- Best practices: Secure key management

**KMS Features**

*Customer Master Keys (CMKs)*
- Symmetric keys: AES-256 encryption
- Asymmetric keys: RSA and ECC keys
- Key material: AWS-managed vs customer-managed
- Key aliases: Human-readable key names

*Key Management*
- Key rotation: Automatic and manual rotation
- Key deletion: Secure key deletion
- Key import: Bringing your own keys
- Multi-Region keys: Replicating keys across regions

#### Data Classification

**Classification with ML Services**
- Automated classification: Using ML to classify data
- Sensitivity levels: Identifying data sensitivity
- Compliance: Meeting data classification requirements
- Tagging: Applying classification tags

**Guardrails Access**
- Access controls: Ensuring only authorized access
- Audit trails: Tracking data access
- Compliance: Meeting regulatory requirements

#### Encryption in Transit

**API-based Services (S3 & DynamoDB)**
- TLS/SSL: Encrypting data in transit
- HTTPS: Secure API communication
- Client-side encryption: Encrypting before transmission

**Database Services (Amazon RDS)**
- TLS connections: Encrypting database connections
- SSL certificates: Managing SSL certificates
- Encrypted connections: Ensuring all connections are encrypted

**Infrastructure Layer (EBS & Nitro)**
- EBS encryption: Encrypting EBS volumes
- Nitro system: Hardware-based encryption
- Performance: Encryption without performance impact

#### Secrets Management - ACM

**AWS Certificate Manager**
- Managing SSL/TLS certificates
- Certificate automation: Automatic certificate renewal
- Private CA: Creating private certificate authorities

#### AWS Secrets Manager & Rotation

**Secrets Manager Overview**
- Centralized secrets: Storing secrets securely
- Automatic rotation: Rotating secrets automatically
- Access control: Controlling who can access secrets
- Audit logging: Tracking secret access

**Rotation Strategies**
- Database credentials: Rotating database passwords
- API keys: Rotating API keys
- Custom rotation: Creating custom rotation logic
- Rotation schedules: Setting rotation frequency

---

### Session 5: Incident Response (11:50 AM+)
**Speakers:** Tinh Truong, Mendel Grabski (Long)

#### Understanding Incidents

**Types of Incidents**
- Breach: Unauthorized access to data or systems
- Hacking: Malicious intrusion into systems
- Downtime: Service unavailability
- Data corruption: Loss or damage to data
- Other security events: Various security-related incidents

#### Security Incident Response for Modern Cloud

**Cloud-Specific Considerations**
- Shared responsibility: Understanding AWS and customer responsibilities
- Cloud-native tools: Using AWS services for incident response
- Automation: Automating incident response
- Scalability: Handling incidents at cloud scale

#### Incident Controls - Security Foundation

**Prevention Controls**
- Security controls: Preventing incidents from occurring
- Best practices: Implementing security best practices
- Compliance: Meeting security requirements

#### Prevention - Nobody Has Time for Incidents

**Key Prevention Strategies**

*Kill Long-lived Credentials*
- Eliminate permanent credentials: Removing long-term access keys
- Use temporary credentials: Preferring STS tokens
- Regular rotation: Rotating any remaining credentials

*Never Expose S3 Buckets Directly*
- Private by default: Keeping buckets private
- Access controls: Using IAM and bucket policies
- Public access: Only when absolutely necessary with proper controls

*Nothing Internet-Facing That Shouldn't Be*
- Minimize attack surface: Reducing publicly accessible resources
- Network segmentation: Isolating resources
- Security groups: Restricting access

*Everything Through Infrastructure as Code*
- Version control: Tracking all infrastructure changes
- Auditability: Knowing what changed and when
- Reproducibility: Consistent infrastructure
- Review process: Code review for infrastructure changes

*Double-Gate High-Risk Changes*
- Approval process: Requiring multiple approvals for risky changes
- Change management: Formal change process
- Testing: Testing changes before production

**Your Guide to Sleep Better**
- Confidence in security: Knowing your security is solid
- Monitoring: Continuous security monitoring
- Automation: Automated security responses
- Best practices: Following security best practices

#### Incident Response Process

**Detection**
- Identifying incidents: Recognizing security events
- Alerting: Getting notified of incidents
- Triage: Prioritizing incidents

**Containment**
- Isolating threats: Preventing spread
- Preserving evidence: Maintaining evidence for analysis
- Communication: Informing stakeholders

**Eradication**
- Removing threats: Eliminating the cause
- Patching vulnerabilities: Fixing security issues
- Cleaning up: Removing compromised resources

**Recovery**
- Restoring services: Getting back to normal operations
- Verification: Ensuring threats are gone
- Monitoring: Increased monitoring post-incident

**Lessons Learned**
- Post-incident review: Analyzing what happened
- Improvements: Identifying areas for improvement
- Documentation: Recording lessons learned

---

## Key Technical Learnings

### Security is Multi-Layered
- Security requires defense in depth with multiple layers
- Each layer addresses different attack vectors
- No single security control is sufficient alone

### Identity is the Foundation
- Strong identity and access management is critical
- Least privilege is essential
- Temporary credentials reduce risk

### Continuous Monitoring is Essential
- You can't protect what you can't see
- Comprehensive logging and monitoring enable detection
- Automation helps respond to threats quickly

### Network Security is Critical
- Network controls are the first line of defense
- Multiple network security layers provide better protection
- Understanding traffic flows helps detect anomalies

### Data Protection is Mandatory
- Encryption at rest and in transit is essential
- Proper key management is critical
- Secrets must be managed securely

### Incident Response Must Be Prepared
- Prevention is best, but incidents will happen
- Having a plan and practicing it is essential
- Automation can speed up response

---

## Personal Takeaways

### Security Mindset
- Learned how layered security on AWS works in practice
- Understand how to combine IAM, logging, network controls, and encryption
- See security as an ongoing process, not a one-time setup

### Practical Skills
- Can now design secure architectures using AWS security services
- Understand how to implement defense in depth
- Know how to monitor and respond to security events

### Best Practices
- The importance of least privilege and temporary credentials
- How to use multiple security layers effectively
- The value of automation in security

### Career Development
- This workshop significantly deepened my understanding of AWS security
- See security as a critical skill for any cloud professional
- Motivated to continue learning about advanced security topics

---

## Event Experience

This workshop was incredibly comprehensive and practical. The depth of coverage on each topic, combined with real-world examples and best practices, made complex security concepts accessible.

The progression from identity management through detection, network security, data protection, and incident response created a complete picture of AWS security. Each session built on previous concepts, reinforcing learning.

The speakers were knowledgeable and provided practical insights beyond just feature descriptions. The real-world examples and case studies helped me understand how to apply these security practices in practice.

This workshop has significantly improved my understanding of how to build secure workloads on AWS, and I'm confident I can apply these learnings to design and implement secure architectures.

#### Event Photos

![Hybrid Networks - VPC and On-Premises Connectivity](/images/event-5/hybrid-networks.png)

![Key Summary - Security Best Practices](/images/event-5/key-summary.png)

![Multi-layer Security - Defense in Depth](/images/event-5/multilayer-security.png)

![Route 53 - DNS Security and Resolution](/images/event-5/route53.png)
