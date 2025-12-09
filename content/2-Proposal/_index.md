---
title: "Proposal"
date: "2025-10-22"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# MAPVIBE - AI-Powered Map Location Discovery Platform
*(Discover dining and other locations in Ho Chi Minh City using natural-language prompts and contextual insights)*

---

## 1. Executive Summary

We are a team of 5 Information Technology students working together to develop a project called MapVibe. MapVibe is an innovative web platform that helps users, especially **GenZ**, find dining locations using natural language based on their **mood and genuine emotions**. For example, instead of searching for "coffee shop", users can ask "I'm feeling sad today, is there any drink place that can help me relieve my sadness?".

The project's goal is to improve traditional search methods and create a more personalized, deeper experience for users. We chose AWS as our cloud platform to leverage powerful, flexible, and cost-effective services. This allows the team to focus maximum resources on developing core features, minimizing infrastructure management burden, while keeping operating costs within the **$200 budget from AWS Free Tier credits**, which is very suitable for a student project.

MapVibe's core feature allows users to query using natural language to find locations that match their mood or specific needs. The system will analyze and return the most suitable suggestions, along with reviews and detailed information.

To achieve this goal, our team will be responsible for the entire process: from design, website development, building and configuring infrastructure on AWS (using services such as **Bedrock**, **Lambda**, **RDS**), to independently compiling the initial dataset of locations.

---

## 2. Problem Statement

### What’s the Problem?

- Traditional map platforms like Google Maps rely on keyword-based searches and static filters, struggling to interpret nuanced, context-rich queries (e.g., “quiet coffee shop near the river with outdoor seating”).
- Users waste time navigating multiple apps to find suitable dining or activity locations.
- Existing solutions lack conversational interfaces and fail to incorporate contextual signals like time, mood, or group size.

### The Solution

MapVibe employs **AWS Bedrock (Titan embedding model, Claude LLM model)** to parse natural-language prompts in Vietnamese and English, converting them into structured queries. It retrieves and ranks results from an internal **RDS (PostgreSQL) database** with geo-indexed place data and vector support features, offering a hybrid interface (conversational search + category filters). User-generated content (reviews, place suggestions) is moderated using **AWS Rekognition**, ensuring safety and quality through advanced AI-driven analysis.

### Benefits and ROI

- **Speed**: Reduces location discovery time from minutes to seconds.
- **Personalization**: Context-aware results based on user preferences and behavior, powered by AI.
- **Automation**: Eliminates manual filtering with AI-driven intent parsing.
- **Scalability**: Global AWS infrastructure ensures low latency and resilience.
- **Cost Efficiency**: Optimized to fit within a $200 credit from AWS Free Tier for the entire development and initial deployment cycle.
- **Commercial Potential**: Opportunities for partnerships with local businesses or integration with internal booking systems.

---

## 3. Solution Architecture

### Overview

User Prompt + Context → **Bedrock Titan Embedding Model** → **Structured Query** → **RDS (PostgreSQL) Search** → **Rank & Cache** → **Web UI Display** → **User Feedback Loop**.  
![Solution Architecture](/images/proposal/Architechture.png)

### AWS Services Used

| Service                   | Function                              |
|---------------------------|---------------------------------------|
| Amazon Route 53           | Domain routing                        |
| AWS Certificate Manager   | SSL/TLS certificates                  |
| AWS WAF                   | Web application firewall              |
| Amazon CloudFront         | Global CDN for static assets          |
| Amazon API Gateway        | Secure RESTful API endpoints           |
| AWS Lambda                | Intent parsing, search, and ranking logic |
| Amazon RDS (PostgreSQL)   | Geo-indexed place data and query caching |
| Amazon S3                 | Storage for photos, logs, and assets   |
| Amazon Cognito            | User authentication and authorization |
| Amazon Bedrock            | Titan embedding model and Claude LLM model for intent parsing and summarization |
| Amazon Rekognition        | AI-driven content moderation for user uploads |
| Amazon Textract           | Extract text from images and documents (menus, signs, etc.) |
| Amazon EventBridge        | Scheduled analytics and badge updates  |
| Amazon CloudWatch         | Monitoring and logging                |

### Component Design

- **Frontend**: Responsive web app (Next.js, bilingual VI/EN, hybrid search UI).
- **Data Ingestion**: Prompts and context processed via API Gateway; user uploads (reviews, photos) moderated by Rekognition’s AI.
- **Data Storage**: RDS (PostgreSQL) for place data with relational database design (ERD), vector support features, and indexing for optimized query speed; S3 for photos and logs.
- **Data Processing**: Lambda microservices handle Bedrock (Titan embedding model and Claude LLM model) calls, query execution, and result ranking.
- **User Management**: Cognito for JWT-based authentication (email/social login); guest users access limited features.
- **Output**: Displays place cards with AI-generated summaries, ratings, photos, and CTAs (e.g., Get Directions, Call).

---

## 4. Technical Implementation

### Implementation Phases

| Phase | Description                                          | Duration   |
|-------|------------------------------------------------------|------------|
| 1     | Define architecture, Bedrock Titan embedding schema, and RDS (PostgreSQL) schema with ERD design | 2 weeks |
| 2     | Estimate costs and optimize caching strategy          | 1 week |
| 3     | Build backend (Lambda, RDS PostgreSQL, Bedrock Titan embedding, Rekognition)| 3 weeks |
| 4     | Develop frontend (Next.js, bilingual, responsive UI)  | 3 weeks |
| 5     | Test and optimize for <10s latency and scalability    | 2 weeks |
| 6     | Launch MVP, deploy via CI/CD (Terraform, GitLab), collect feedback        | 2 weeks |

### Technical Requirements

- **Edge Devices**: Modern browsers (Chrome, Safari, Firefox) with PWA-ready responsive UI.
- **Cloud**: AWS Route 53, ACM, WAF, CloudFront, API Gateway, Lambda, RDS (PostgreSQL with vector support), S3, Cognito, Bedrock (Titan embedding, Claude LLM), Rekognition, Textract, EventBridge, CloudWatch.
- **Tools & Frameworks**: Next.js (App Router), TypeScript, Terraform for infrastructure-as-code, GitLab for CI/CD.

---

## 5. Timeline & Milestones

| Period              | Activities                                                  |
|---------------------|-------------------------------------------------------------|
| Pre-Development (Month 0 - Sept 2025) | Research Ho Chi Minh City venue datasets for RDS (PostgreSQL)       |
| Month 1 (Oct 2025) | Build backend MVP with Bedrock Titan embedding model and RDS (PostgreSQL)            |
| Month 2 (Nov 2025)  | Implement caching, develop frontend integration            |
| Month 3 (Nov 2025)  | Launch public beta, optimize performance, collect feedback  |
| Post-Launch (Dec 2025) | Add advanced features (e.g., ML-based ranking, offline mode)|

---

## 6. Budget Estimation

### Resource Investment Time Estimation

We estimate that each team member will contribute approximately 20 hours per week to the project. With each phase lasting 2 weeks, the total time investment is estimated as follows:

| Project Phase | Total Estimated Hours |
|:--:|:--:|
| Phase 1: Platform Setup | 200 hours (5 people * 20 hours/week * 2 weeks) |
| Phase 2: Core Feature Development | 200 hours (5 people * 20 hours/week * 2 weeks) |
| Phase 3: Completion and Deployment | 200 hours (5 people * 20 hours/week * 2 weeks) |
| **Total Hours** | **600 hours** |
| **Total Financial Cost** | **$0** |

### Resource Contribution Distribution

The direct financial cost of the project is negligible and fully covered by credits. The main contribution comes from the team's time and support from AWS.

| Participant | Contribution | % Contribution (Total Value) |
|:--|:--|:--|
| Client (Internship Program) | - Learning opportunities and practical experience. | - |
| Partner (Student Team) | - Time and effort (estimated 600 hours). | - |
| AWS | - $200 credit. <br> - Services in Free Tier package. | 100% (financial cost) |

### Cost Optimization Measures
- **Free-Tier Utilization**: Leverage AWS free tiers for Lambda, RDS, S3, CloudFront, Rekognition, and Cognito to minimize costs.
- **Aggressive Caching for Bedrock**: Achieve a high cache hit rate to reduce AI token costs.
- **Batch Rekognition Processing**: Non-real-time image checks to save costs.
- **Optimized RDS Usage**: Use PostgreSQL with proper indexing to minimize query costs.
- **Static Asset Caching**: Minimize outbound data transfer costs through CloudFront.

### Budget Control
- The entire project operates within the **$200 credit from AWS Free Tier**.
- All infrastructure costs are covered by AWS credits and free tier services.
- No direct financial costs are incurred by the team.

---

## 7. Risk Assessment

| Risk                            | Impact | Probability | Mitigation                              |
|---------------------------------|--------|-------------|----------------------------------------|
| RDS data inconsistency          | High   | Medium      | Regular data validation and backups    |
| Inaccurate Titan embedding parsing (VN/EN)  | Medium | Low         | Predefined prompt templates, validation |
| Scalability under high load     | Medium | Medium      | Serverless auto-scaling, caching       |
| Privacy concerns (location data)| High   | Low         | Explicit user consent, anonymized queries |
| Budget overrun                  | High   | Medium      | Strict monitoring, use of free tiers, cost alerts |
| AWS Bedrock service dependency (Titan, Claude)  | High   | Low         | Alternative fallback mechanisms, cached results |
| GitLab platform dependency      | Medium | Low         | Regular backups, alternative repository options |
| Initial data quality            | Medium | Medium      | Data validation processes, user feedback integration |

**Contingency Plans**: Use cached RDS results or local JSON fallback for demos. Implement IP-based rate limits for unauthenticated users. Monitor AWS costs weekly to prevent budget overruns.

---

## 8. Expected Outcomes

### Project Success Criteria

To ensure the MapVibe project succeeds, we have set specific, measurable success criteria:

- **Complete Infrastructure Deployment**: Successfully and securely deploy the entire system architecture to AWS, including all planned services such as VPC, Subnet, RDS, Lambda, S3, CloudFront, API Gateway, and Cognito.
- **Core Search Feature Works Effectively**: The natural language search feature using AWS Bedrock (Titan embedding model, Claude LLM model) and RDS PostgreSQL must be able to understand and return relevant, meaningful results for at least **90%** of common user queries.
- **Cost Optimization**: Total AWS service usage costs throughout development and initial deployment do not exceed the $200 credit from AWS Free Tier package.
- **Product Launch (MVP)**: Complete and launch a minimum viable product (MVP) version of the MapVibe website for the target user group (GenZ) on both **desktop and iOS, Android platforms**. Additionally, include an **administrator dashboard** for managing content and users.
- **Collect Positive Feedback**: After launch, collect at least 50 new location suggestions from users in the first month, demonstrating community interaction and engagement.

### Technical Improvements
- **Mood-Based Conversational Search**: Natural-language support for Vietnamese and English with <10s latency, powered by Bedrock (Titan embedding model and Claude LLM model), understanding user emotions and moods.
- **AI Summaries**: Bedrock-generated place overviews, refreshed every 7 days or after 10 new reviews.
- **Scalability**: Serverless architecture with global CDN delivery via CloudFront.
- **Moderation**: Rekognition's AI ensures safe user-generated content (reviews, photos).
- **Relational Database**: PostgreSQL with optimized indexing for fast query performance.

### Long-Term Value
- **Personalization**: ML-based re-ranking and user behavior analysis based on mood and preferences.
- **Offline Support**: PWA for offline shortlisting of venues.
- **Extensibility**: Potential integration with internal booking systems.
- **Contextual Expansion**: Recommendations based on weather, events, social trends, and user emotions.

---

### Attachments / References
- [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=b574c31813807522d949cf5adca64b41612e12c7)
- [GitLab Repository](https://gitlab.com/4n1d/mapvibe)

## 9. IMPORTANT: Our Proposal Docs Version 
- [Proposal Docs Version](https://docs.google.com/document/d/10YCwRMZcYZ6tFfRam9gASe-DpZf98DxW/edit)
- [Related Documents](https://drive.google.com/drive/u/0/folders/1cdBYgwzBA4Vl9ww_fCPXmbsKToTKgH4L)
