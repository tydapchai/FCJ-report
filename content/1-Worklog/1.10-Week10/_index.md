---
title: "Week 10 Worklog"
date: "2025-09-11"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### OBJECTIVES IN WEEK 10:
- Explore and architect the Backend system for Hybrid Search functionality, integrating both keyword-based and semantic search approaches for the project.
- Gain proficiency in end-to-end Serverless architecture: From event-driven processing (S3 triggers), data storage (DynamoDB) to API development (API Gateway).
- Implement an automated CI/CD workflow for Serverless applications leveraging AWS CodePipeline.
- Develop hands-on expertise in Serverless application Monitoring and Distributed Tracing using CloudWatch and X-Ray.

### TASKS OF WEEK 10:
| Day | Task | Start Date | End Date | References |
|-----|------|------------|----------|------------|
| Mon | - Team Project Meeting: Backend Development - Hybrid Search Engine (Text search + semantic search): <br> &emsp; - Investigate best practices and academic papers on hybrid search systems <br> &emsp; - Draft initial hybrid search engine architecture | 10/11/2025 | 10/11/2025 | [Paper](https://arxiv.org/abs/2210.11934) <br> [Medium Article](https://medium.com/@zilliz_learn/hybrid-search-combining-full-text-and-semantic-search-explained-1f6d25c628da) <br> [Meilisearch](https://www.meilisearch.com/blog/hybrid-search) <br> [Google Vertex AI](https://cloud.google.com/vertex-ai/docs/vector-search/overview) |
| Tue | - Practice Lab 22: Serverless - Lambda interaction with S3 and DynamoDB <br> &emsp; + Overview <br> &emsp; + Image Processing and Optimization on AWS <br> &emsp;&emsp; * Build Image Processing Lambda Function <br> &emsp;&emsp; * Provision S3 Bucket <br> &emsp;&emsp; * Configure IAM Policy for Lambda <br> &emsp;&emsp; * Validate Lambda Function <br> &emsp; + Store data in Amazon DynamoDB <br> &emsp;&emsp; * Provision and Manage DynamoDB Tables <br> &emsp;&emsp; * Build Lambda Function for Data Insertion <br> &emsp; + Resource Cleanup | 11/11/2025 | 11/11/2025 | [Lab 22 Intro](https://000022.awsstudygroup.com/vi/1-introduce/) <br> [Resize Function](https://000022.awsstudygroup.com/vi/2-resizeimage/) <br> [DynamoDB Write](https://000022.awsstudygroup.com/vi/3-writedatatodynamodb/) |
| Wed | - Practice Lab 23: Serverless - Building Front-end to consume API Gateway <br> &emsp; + Overview of API Gateway / DynamoDB <br> &emsp; + Deploy front-end application <br> &emsp; + Configure Lambda functions <br> &emsp;&emsp; * Provision DynamoDB table <br> &emsp;&emsp; * Deploy Lambda functions <br> &emsp;&emsp;&emsp; - Lambda for data insertion <br> &emsp;&emsp;&emsp; - Lambda for data retrieval <br> &emsp;&emsp;&emsp; - Lambda for data deletion <br> &emsp; + Configure API Gateway <br> &emsp;&emsp; * Define API methods <br> &emsp;&emsp; * Enable and configure CORS <br> &emsp; + Validate API using Postman <br> &emsp; + Validate API via front-end <br> &emsp; + Resource Cleanup | 12/11/2025 | 12/11/2025 | [Lab 23 Intro](https://000023.awsstudygroup.com/vi/1-introduce/) <br> [Deploy Frontend](https://000023.awsstudygroup.com/vi/2-deployfrontend/) <br> [API Gateway](https://000023.awsstudygroup.com/vi/4-apigateway/) <br> [Postman Test](https://000023.awsstudygroup.com/vi/5-testwithpostman/) |
| Thu | - Team Project Meeting: Backend Development - Hybrid Search Engine (Text search + semantic search): <br> &emsp; - Execute and validate hybrid search engine with collected dataset <br> &emsp; - Complete hybrid search engine architecture design | 13/11/2025 | 13/11/2025 | [Supabase AI](https://supabase.com/docs/guides/ai) <br> [MongoDB Hybrid](https://www.mongodb.com/docs/atlas/atlas-vector-search/tutorials/reciprocal-rank-fusion/) <br> [AWS OpenSearch](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/hybrid-search.html) <br> [Amazon Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base-hybrid.html) |
| Fri | - Practice Lab 24: Serverless - CI/CD with CodePipeline <br> &emsp; + Environment Setup <br> &emsp; + Configure SAM pipeline <br> &emsp;&emsp; * Initialize Git repository <br> &emsp;&emsp; * Build SAM pipeline <br> &emsp; + Configure front-end pipeline <br> &emsp;&emsp; * Initialize Git repository <br> &emsp;&emsp; * Build deployment pipeline <br> &emsp; + Verify web application functionality <br> &emsp; + Cleanup <br> - Practice Lab 25: Serverless - Observability with CloudWatch and X-Ray <br> &emsp; + Environment Setup <br> &emsp; + Monitoring with CloudWatch <br> &emsp;&emsp; * Troubleshoot using CloudWatch Logs <br> &emsp;&emsp; * Implement custom metrics <br> &emsp;&emsp; * Configure CloudWatch Alarms <br> &emsp; + Distributed tracing with X-Ray <br> &emsp; + Cleanup | 14/11/2025 | 14/11/2025 | [Lab 24 Intro](https://000024.awsstudygroup.com/vi/1-introduce/) <br> [SAM Pipeline](https://000024.awsstudygroup.com/vi/2-sampipeline/) <br> [Lab 25 Intro](https://000025.awsstudygroup.com/vi/1-introduce/) <br> [CloudWatch](https://000025.awsstudygroup.com/vi/2-cloudwatch/) <br> [X-Ray](https://000025.awsstudygroup.com/vi/3-xray/) |

### ACHIEVEMENTS IN WEEK 10:
1. Completed the design and validation of the Hybrid Search Engine architecture, combining traditional keyword search with vector-based (Semantic) search capabilities.

2. Developed a comprehensive Serverless Backend pipeline: Implemented automated image processing using S3 event triggers and managed NoSQL data operations with DynamoDB.

3. Deployed a complete Full-stack Serverless Application: Integrated Frontend with Backend services through API Gateway and Lambda, successfully resolving CORS configuration challenges.

4. Established an automated DevOps pipeline (CI/CD) for Serverless applications, enabling seamless and reliable deployment of both backend code and frontend assets.

5. Improved system observability by implementing Monitoring Dashboards (CloudWatch) and Request Tracing (X-Ray) for efficient debugging and performance analysis.
