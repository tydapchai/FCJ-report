---
title: "Week 3 Worklog"
date: "2025-09-11"
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---


### Week 3 Objectives:

* Deep dive into AWS Compute services: EC2, Load Balancing, and Auto-Scaling
* Understand AWS Database models and migration strategies
* Learn about modern compute evolution: Containers and Serverless
* Master EC2 instance configuration and connection methods

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - **AWS EC2 Overview:** <br>&emsp; + Instance categories (General Purpose, Compute Optimized, Memory Optimized) <br>&emsp; + Key configuration components (AMI, Key Pair, VPC, Security Group, EBS) <br>&emsp; + Connection methods (SSH, Session Manager, EC2 Instance Connect) | 21/09/2025 | 21/09/2025      | AWS Documentation |
| 3   | - **Load Balancing & Auto-Scaling:** <br>&emsp; + Load Balancer types (ALB, NLB, CLB, GWLB) <br>&emsp; + How load balancing works across target groups <br>&emsp; + EC2 Auto Scaling concepts and benefits <br>&emsp; + Integration between Load Balancing and Auto-Scaling | 22/09/2025 | 22/09/2025      | AWS Documentation |
| 4   | - **Evolution of Compute:** <br>&emsp; + Traditional compute vs Modern compute needs <br>&emsp; + Container services (ECS, EKS) <br>&emsp; + Serverless compute (Lambda, Fargate) <br>&emsp; + Containers vs Serverless comparison | 23/09/2025 | 23/09/2025      | AWS Documentation |
| 5   | - **AWS Database Models:** <br>&emsp; + Relational databases (RDS, Aurora) <br>&emsp; + NoSQL databases (DynamoDB, DocumentDB) <br>&emsp; + Memory-based databases (MemoryDB for Redis) <br>&emsp; + EC2-hosted databases vs AWS-managed | 24/09/2025 | 26/09/2025     | AWS Documentation |
| 6   | - **Database Migration:** <br>&emsp; + Migration phases and strategies <br>&emsp; + AWS migration tools (DMS, Snow Family, DataSync, SCT) <br>&emsp; + Choosing the right migration tool for different scenarios | 26/09/2025 | 27/09/2025      | AWS Documentation |


### How Load Balancing works

1. Users send requests
2. Requests hit the load balancer
3. The primary target group is served first by the Application Load Balancer
4. When demand increases, the load balancer activates the secondary target group and distributes traffic across all instances

![How load balancing works](/images/week3-worklog/load-balancing.png)


### How Auto-Scaling works

1. Users send requests
2. Requests are routed to the EC2 Auto Scaling service
3. The service routes requests to active EC2 instances
4. If demand increases, new EC2 instances are added to handle the additional load
5. As demand decreases, the newly added instances are terminated

![How auto-scaling works](/images/week3-worklog/auto-scaling.png)


### Week 3 Achievements:

* **Mastered AWS EC2 Fundamentals:**
  * Understood EC2 instance categories: General Purpose, Compute Optimized, Memory Optimized, Storage Optimized, Accelerated Computing, and HPC
  * Learned key configuration components: AMI, Key Pairs, VPC, Security Groups, and EBS volumes
  * Gained proficiency in EC2 connection methods: SSH Client, AWS Session Manager, and EC2 Instance Connect

* **Comprehensive Understanding of Load Balancing & Auto-Scaling:**
  * Mastered different Load Balancer types: ALB (Layer 7), NLB (Layer 4), CLB (Legacy), and GWLB (Virtual Appliances)
  * Understood how load balancing distributes traffic across primary and secondary target groups
  * Learned EC2 Auto Scaling concepts and how it automatically adjusts compute capacity
  * Recognized the integration between Load Balancing and Auto-Scaling for resilient architectures

* **Evolution of Compute Services:**
  * Distinguished between traditional compute (EC2) and modern compute needs
  * Explored container services: Amazon ECS (AWS-native) and Amazon EKS (Kubernetes-managed)
  * Understood serverless compute: AWS Lambda (function-based) and AWS Fargate (container-based)
  * Analyzed the trade-offs between containers and serverless compute for different use cases

* **AWS Database Models Expertise:**
  * **Relational Databases:** Mastered Amazon RDS and Aurora for structured data and complex SQL queries
  * **NoSQL Databases:** Learned DynamoDB (key-value store) and DocumentDB (MongoDB-compatible) for flexible schemas
  * **Memory-Based Databases:** Understood MemoryDB for Redis for ultra-fast data retrieval and caching
  * **EC2-Hosted vs AWS-Managed:** Evaluated trade-offs between control and automation

* **Database Migration Strategies:**
  * Understood migration phases: Assessment, Preparation, Execution, Validation, and Optimization
  * Learned AWS migration tools: DMS (online migration), Snow Family (offline transfer), DataSync (automated sync), and SCT (schema conversion)
  * Developed ability to choose appropriate migration tools based on specific scenarios and requirements

* **Key Insights Gained:**
  * EC2 provides flexible, scalable virtual machines integrated with AWS networking, storage, and security
  * Load Balancers handle traffic distribution while Auto-Scaling handles resource elasticity
  * Containers suit predictable workloads needing control, while Serverless excels in event-driven scenarios
  * AWS offers multiple database models enabling optimal balance between control, scalability, and automation
