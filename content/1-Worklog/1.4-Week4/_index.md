---
title: "Week 4 Worklog"
date: "2025-09-11"
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Study and document AWS Database Migration Services (DMS, SCT, Snow Family, DataSync)
* Study and document AWS Network Services (VPC, Security, Private/Hybrid connectivity, Route 53, CloudFront)

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | ------------------ |
| 1   | Research and outline database migration objectives and constraints | 10/22/2025 | 10/22/2025 | AWS Documentation |
| 2   | Study AWS Database Migration Services: DMS, SCT, Snow Family, DataSync; map use cases | 10/22/2025 | 10/22/2025 | AWS Documentation |
| 3   | Document migration phases: assessment, preparation, execution, validation, optimization | 10/22/2025 | 10/22/2025 | AWS Documentation |
| 4   | Study AWS Network Services: VPC, security layers, VPC Endpoints/PrivateLink, VPN/Direct Connect | 10/22/2025 | 10/22/2025 | AWS Documentation |
| 5   | Summarize Route 53 and CloudFront roles; create diagrams and notes | 10/22/2025 | 10/22/2025 | AWS Documentation |


### Week 4 Achievements:

* Gained comprehensive understanding of AWS Database Migration Services:
  * Database migration process and phases
  * AWS migration tools (DMS, SCT, Snow Family, DataSync)
  * Best practices for different migration scenarios
  * Migration planning and execution strategies

* Mastered AWS Network Services fundamentals:
  * VPC architecture and components
  * Network security (Security Groups, NACLs)
  * Private connectivity options (VPC Endpoints, PrivateLink)
  * Hybrid connectivity solutions (VPN, Direct Connect)
  * Global services (Route 53, CloudFront)

* Consolidated notes and visuals for future implementation and reference.


### Database Migration Services in AWS

* Concept: Move data from on‑premises or other clouds to AWS in phases (assessment → preparation → execution → validation → optimization)
* Why: Legacy limits, analytics/AI needs, and desire for a unified data layer
* Services and when to use:
  * DMS: Online, near‑zero downtime replication for heterogeneous/homogeneous migrations
  * Snow Family: Petabyte‑scale offline transfers with encryption and edge processing
  * DataSync: Automated, high‑speed ongoing data syncs (S3/EFS/EBS)
  * SCT: Schema conversion and assessment between database engines

![Database Migration Services in AWS](/images/week4-worklog/database-migration.png)


#### What is Database Migration?

* Move data from one environment to another (on‑premises → AWS, cross‑cloud, cross‑engine)
* Similar to moving offices: planning → preparation → execution → validation → optimization

#### Why Data Migration is Needed

* Legacy systems do not meet modern scalability/performance
* AI/ML and analytics need powerful compute and storage
* Centralized, unified data management layer across sources

#### Phases of a Migration Project

| Step        | Description                                             |
| ----------- | ------------------------------------------------------- |
| Assessment  | Analyze source data, formats, dependencies              |
| Preparation | Develop migration plan and organize data                |
| Execution   | Run migration tools and transfer data                   |
| Validation  | Verify data integrity and perform post‑migration tests  |
| Optimization| Tune performance in the new AWS environment             |

#### AWS Migration Tools and Services

| Service | Purpose | Key Features | Best For |
| --- | --- | --- | --- |
| AWS Database Migration Service (DMS) | Online data migration for heterogeneous/homogeneous databases | Multi‑AZ replication, near‑zero downtime, validation | Large‑scale, complex migrations |
| AWS Snow Family | Offline physical transfer at petabyte scale | Secure devices, encryption, edge processing | Limited bandwidth or remote/edge |
| AWS DataSync | Automated, high‑speed transfer between on‑premises and AWS | Parallel processing, S3/EFS integration, API automation | Frequent, large‑scale, ongoing syncs |
| AWS Schema Conversion Tool (SCT) | Schema/code conversion between engines | Auto mapping, rules, validation, live diagnostics | Heterogeneous migrations (e.g., Oracle → PostgreSQL) |

#### Choosing the Right Tool

| Scenario | Recommended Service |
| --- | --- |
| Migrate large, complex production databases | DMS |
| Transfer petabyte‑scale data physically/offline | Snow Family |
| Automate recurring data transfers | DataSync |
| Convert schema between different database types | Schema Conversion Tool |

> Key Insight: AWS provides complementary tools across all stages to migrate securely, efficiently, and with minimal downtime.


### AWS Network Services Overview

* VPC: Isolated virtual network (subnets, route tables, gateways)
* Network Security: Security Groups (instance level) and NACLs (subnet level)
* Private Connectivity: AWS PrivateLink, VPC Endpoints for private access to AWS services
* Hybrid: Direct Connect and Site‑to‑Site VPN for on‑premises connectivity
* DNS: Amazon Route 53 for domain management and health checks
* CDN: CloudFront for global caching, performance, and DDoS protections

![AWS Network Services Overview](/images/week4-worklog/network-services.png)

#### Purpose

* Enable secure, scalable, fast communication between users, apps, and cloud resources
* Core services: VPC, VPN, Direct Connect, Route 53, CloudFront

#### Amazon Virtual Private Cloud (VPC)

* Private, logically isolated network in a Region with IPv4/IPv6 and custom CIDRs
* Control components:
  * Subnets – subdivisions of the VPC
  * Route tables – routing rules
  * Gateways – internet/NAT/VPN/Direct Connect
* Types:

| Type | Description |
| --- | --- |
| Default VPC | Auto‑created, internet‑accessible with predefined subnets |
| Custom VPC | User‑defined; requires manual routing and internet configuration |

![Understanding key VPC concepts](/images/week4-worklog/vpc-concepts.png)

#### Network Security

| Component | Function | Scope |
| --- | --- | --- |
| Security Groups | Virtual firewall controlling instance‑level traffic | Instance‑level |
| Network ACLs | Stateless firewall controlling subnet‑level traffic | Subnet‑level |

![Route tables](/images/week4-worklog/route-tables.png)


#### Private Connectivity

| Feature | Description |
| --- | --- |
| VPC Endpoints | Private access to AWS services without public IPs |
| AWS PrivateLink | Secure, private communication between VPCs, AWS services, and on‑premises without internet gateways |

![VPC endpoints](/images/week4-worklog/vpc-endpoints.png)

![AWS PrivateLink](/images/week4-worklog/privatelink.png)

#### Hybrid Connectivity

| Service | Description | Best Use Case |
| --- | --- | --- |
| AWS VPN | Encrypted internet connection between on‑premises and AWS | Smaller/flexible workloads |
| AWS Direct Connect | Dedicated, high‑bandwidth physical link bypassing the internet | Consistent, secure enterprise workloads |

#### Amazon Route 53 (DNS)

* Scalable DNS: domain registration, routing, health checks; supports traffic distribution and failover

![Amazon Route 53](/images/week4-worklog/route53.png)

#### Amazon CloudFront (CDN)

* Global CDN caching at edge locations to reduce latency and improve security
* Features: low‑latency web/API delivery, optimized streaming, autoscaling for spikes, HTTPS + AWS Shield

![Content Delivery Networks (CDNs)](/images/week4-worklog/cdn.png)

![Amazon CloudFront](/images/week4-worklog/cloudfront.png)

#### Summary – How They Work Together

| Layer | Service | Function |
| --- | --- | --- |
| Networking Core | VPC | Define private cloud network |
| Secure Connectivity | VPN, Direct Connect | Connect on‑premises → AWS |
| Name Resolution | Route 53 | Domain → IP mapping |
| Content Delivery | CloudFront | Global caching and speed optimization |

> Key Insight: Combining VPC isolation, private links, hybrid connectivity, and CDN acceleration delivers secure, high‑performance global networking on AWS.
