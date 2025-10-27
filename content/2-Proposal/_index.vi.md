---
title: "Proposal"
date: "2025-10-22"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
# MAPVIBE

**AI-Powered Map Location Discovery Platform**  
*(Discover dining and other locations in Ho Chi Minh City using natural-language prompts and contextual insights)*

---

## 1. Executive Summary

MapVibe is an AI-driven web platform launched in **Ho Chi Minh City** to transform location discovery, enabling users to find venues through natural-language prompts (e.g., “find a luxury rooftop restaurant with city view open until midnight” or “quiet coffee shop near the river with outdoor seating”). The platform harnesses **Amazon Bedrock’s Large Language Models (LLMs)** to interpret user intent, integrating real-time contextual factors like location, time, and preferences, and retrieves data from an internal **DynamoDB database**. Built on a **serverless AWS architecture**, MapVibe delivers **low latency (<10s)**, **high accuracy (≥85% match satisfaction)**, and **cost efficiency (<$200 for initial 8-week development and demo cycle, completed by October 22, 2025)**. Authenticated users enjoy personalized recommendations, the ability to contribute reviews, and access to moderation tools, all enhanced by AI technologies.

---

## 2. Problem Statement

### What’s the Problem?

- Traditional map platforms like Google Maps rely on keyword-based searches and static filters, struggling to interpret nuanced, context-rich queries (e.g., “quiet coffee shop near the river with outdoor seating”).
- Users waste time navigating multiple apps to find suitable dining or activity locations.
- Existing solutions lack conversational interfaces and fail to incorporate contextual signals like time, mood, or group size.

### The Solution

MapVibe employs **AWS Bedrock LLMs** to parse natural-language prompts in Vietnamese and English, converting them into structured queries. It retrieves and ranks results from an internal **DynamoDB database** with geo-indexed place data, offering a hybrid interface (conversational search + category filters). User-generated content (reviews, place suggestions) is moderated using **AWS Rekognition**, ensuring safety and quality through advanced AI-driven analysis.

### Benefits and ROI

- **Speed**: Reduces location discovery time from minutes to seconds.
- **Personalization**: Context-aware results based on user preferences and behavior, powered by AI.
- **Automation**: Eliminates manual filtering with AI-driven intent parsing.
- **Scalability**: Global AWS infrastructure ensures low latency and resilience.
- **Cost Efficiency**: Optimized to fit within a $200 budget for the initial 8-week cycle, completed by October 22, 2025.
- **Commercial Potential**: Opportunities for partnerships with local businesses or integration with internal booking systems.

---

## 3. Solution Architecture

### Overview

User Prompt + Context → **Bedrock LLM Intent Parsing** → **Structured Query** → **DynamoDB Search** → **Rank & Cache** → **Web UI Display** → **User Feedback Loop**.  
![Solution Architecture](/images/proposal/architecture.png)

### AWS Services Used

| Service                   | Function                              |
|---------------------------|---------------------------------------|
| Amazon Route 53           | Domain routing                        |
| AWS Certificate Manager   | SSL/TLS certificates                  |
| AWS WAF                   | Web application firewall              |
| Amazon CloudFront         | Global CDN for static assets          |
| Amazon API Gateway        | Secure RESTful API endpoints           |
| AWS Lambda                | Intent parsing, search, and ranking logic |
| Amazon DynamoDB           | Geo-indexed place data and query caching |
| Amazon S3                 | Storage for photos, logs, and assets   |
| Amazon Cognito            | User authentication and authorization |
| Amazon Bedrock            | LLM for intent parsing and summarization |
| Amazon Rekognition        | AI-driven content moderation for user uploads |
| Amazon EventBridge        | Scheduled analytics and badge updates  |
| Amazon CloudWatch         | Monitoring and logging                |

### Component Design

- **Frontend**: Responsive web app (Next.js, bilingual VI/EN, hybrid search UI).
- **Data Ingestion**: Prompts and context processed via API Gateway; user uploads (reviews, photos) moderated by Rekognition’s AI.
- **Data Storage**: DynamoDB for place data and cached queries (24-hour TTL); S3 for photos and logs.
- **Data Processing**: Lambda microservices handle Bedrock LLM calls, query execution, and result ranking.
- **User Management**: Cognito for JWT-based authentication (email/social login); guest users access limited features.
- **Output**: Displays place cards with AI-generated summaries, ratings, photos, and CTAs (e.g., Get Directions, Call).

---

## 4. Technical Implementation

### Implementation Phases

| Phase | Description                                          | Duration   |
|-------|------------------------------------------------------|------------|
| 1     | Define architecture, Bedrock prompt schema, and DynamoDB schema | Completed (2 weeks) |
| 2     | Estimate costs and optimize caching strategy          | Completed (1 week) |
| 3     | Build backend (Lambda, DynamoDB, Bedrock, Rekognition)| Completed (3 weeks) |
| 4     | Develop frontend (Next.js, bilingual, responsive UI)  | Completed (3 weeks) |
| 5     | Test and optimize for <10s latency and scalability    | Completed (2 weeks) |
| 6     | Launch MVP, deploy via CI/CD, collect feedback        | Ongoing (started October 22, 2025) |

### Technical Requirements

- **Edge Devices**: Modern browsers (Chrome, Safari, Firefox) with PWA-ready responsive UI.
- **Cloud**: AWS Route 53, ACM, WAF, CloudFront, API Gateway, Lambda, DynamoDB, S3, Cognito, Bedrock, Rekognition, EventBridge, CloudWatch.
- **Tools & Frameworks**: Next.js (App Router), TypeScript, AWS CDK for infrastructure-as-code, GitHub Actions for CI/CD.

---

## 5. Timeline & Milestones

| Period              | Activities                                                  |
|---------------------|-------------------------------------------------------------|
| Pre-Development (Month 0) | Research Ho Chi Minh City venue datasets for DynamoDB       |
| Month 1 (Sept 2025) | Build backend MVP with Bedrock LLM and DynamoDB            |
| Month 2 (Oct 2025)  | Implement caching, develop frontend integration            |
| Month 3 (Oct 2025)  | Launch public beta, optimize performance, collect feedback  |
| Post-Launch (Oct 2025 onward) | Add advanced features (e.g., ML-based ranking, offline mode)|

---

## 6. Budget Estimation

### Cloud Infrastructure Costs

| AWS Service           | Cost/Month (USD) | Description              |
|-----------------------|------------------|--------------------------|
| Lambda                | 15               | API + LLM logic          |
| DynamoDB              | 10               | Cached query store       |
| S3                    | 5                | Logs, static files       |
| API Gateway           | 10               | Request routing          |
| Cognito               | 5                | Auth MAU                 |
| CloudFront            | 10               | Hosting/CDN              |
| Bedrock (LLM tokens)  | 15               | Prompt parsing           |
| Rekognition           | 5                | Batch image moderation   |
| CloudWatch            | 5                | Error-only logging       |
| **Total**             | **≈ 80/month**   | **≈ 160/8 weeks**        |

### Cost Optimization Measures
- **Free-Tier Utilization**: Leverage AWS free tiers for Lambda, DynamoDB, S3, CloudFront, Rekognition, and Cognito to minimize costs.
- **Aggressive Caching for Bedrock**: Achieve a 95% cache hit rate to reduce AI token costs from $120 to <$15/month.
- **Batch Rekognition Processing**: Non-real-time image checks save ~$80 over 8 weeks.
- **Simplified Load Testing**: 100 users × 10 min scenario instead of 300 × 30 min reduces compute costs.
- **Reduced CloudWatch Logging**: Error-only logs save $50+ over 8 weeks.
- **No Provisioned Concurrency**: Avoids idle Lambda costs.
- **Environment Variables**: Use instead of Secrets Manager to eliminate secret storage charges.
- **On-Demand DynamoDB Mode**: All reads/writes free under tier.
- **Disabled Origin Shield**: Saves CloudFront overhead.
- **Static Asset Caching**: Minimizes outbound data transfer costs.

### Recommended Budget Scenarios
To ensure the MapVibe platform operates efficiently within the $200 AWS budget over the initial 8-week development and demo cycle (completed by October 22, 2025), we recommend the following scenarios based on varying levels of optimization and resource usage:

- **Minimal Scenario**: Focuses on essential features with maximum reliance on free tiers. This includes disabling non-critical services like WAF if not needed, limiting Bedrock invocations to cached queries only (targeting 98%+ cache hit rate), and conducting no load testing. Estimated cost: <$50 over 8 weeks. Suitable for initial prototyping but may compromise demo reliability due to potential untested scalability issues.

- **Recommended Scenario**: Balances cost and reliability by incorporating all key optimization measures listed above. This scenario utilizes aggressive caching (95% hit rate for Bedrock), batch processing for Rekognition, simplified load testing (100 users × 10 min), and error-only logging in CloudWatch. It ensures low latency and resilience while staying well under budget. Estimated cost: ~$100-150 over 8 weeks. Ideal for the MVP demo launched on October 22, 2025, providing a robust experience without unnecessary expenses.

- **Enhanced Scenario**: Includes additional provisions for higher usage post-launch, such as provisioned concurrency for Lambda during peak times and full logging in CloudWatch for detailed debugging. This increases costs slightly but enhances performance monitoring and scalability testing (e.g., 300 users × 30 min loads). Estimated cost: ~$180-200 over 8 weeks. Recommended for ongoing operations after October 22, 2025, if extended demos or higher traffic is anticipated, still within the overall budget cap.

Recommendation: The Recommended Scenario was successfully implemented for the MVP launch on October 22, 2025, ensuring optimal demo reliability, scalability, and cost control within the $200 budget. For ongoing operations, consider transitioning to the Enhanced Scenario as needed.

### Cost Control & Monitoring
- Create billing alerts and enable AWS Cost Explorer.
- Tag all resources (Project=MapVibe, Environment=Dev).
- Review weekly:
  - CloudFront data > 50 GB/week
  - Bedrock cache hit < 90%
  - Lambda invocations > 100K/week
  - Total cost > $15/week

---

## 7. Risk Assessment

| Risk                            | Impact | Probability | Mitigation                              |
|---------------------------------|--------|-------------|----------------------------------------|
| DynamoDB data inconsistency     | High   | Medium      | Regular data validation and backups    |
| Inaccurate LLM parsing (VN/EN)  | Medium | Low         | Predefined prompt templates, validation |
| Scalability under high load     | Medium | Medium      | Serverless auto-scaling, caching       |
| Privacy concerns (location data)| High   | Low         | Explicit user consent, anonymized queries |

**Contingency Plans**: Use cached DynamoDB results or local JSON fallback for demos. Implement IP-based rate limits for unauthenticated users.

---

## 8. Expected Outcomes

### Technical Improvements
- **Conversational Search**: Natural-language support for Vietnamese and English with <10s latency, powered by Bedrock LLMs.
- **AI Summaries**: Bedrock-generated place overviews, refreshed every 7 days or after 10 new reviews.
- **Scalability**: Serverless architecture with global CDN delivery via CloudFront.
- **Moderation**: Rekognition’s AI ensures safe user-generated content (reviews, photos).

### Long-Term Value
- **Personalization**: ML-based re-ranking and user behavior analysis.
- **Offline Support**: PWA for offline shortlisting of venues.
- **Extensibility**: Potential integration with internal booking systems.
- **Contextual Expansion**: Recommendations based on weather, events, or social trends.

---

### Attachments / References
- [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=12f225883db76aa012f87014f9994e8bcb304430)
- [GitHub Repository](https://github.com/4N1D/aws-workshop)
- [Related Documents](https://drive.google.com/drive/folders/1LtBMw0791vFCO5fvBHdWg24JyUWVCEXF?usp=sharing)