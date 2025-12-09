---
title : "Introduction"
date: 2025-09-09
weight : 1
chapter : false
pre : " <b> 5.1. </b> "

---

#### About MapVibe

**MapVibe** is an AI-powered location discovery platform that helps users find dining and activity locations in Ho Chi Minh City using natural language queries. Instead of traditional keyword searches, users can express their needs in conversational language, such as "I'm feeling sad today, is there any drink place that can help me relieve my sadness?"

The platform leverages AWS AI services including:
- **AWS Bedrock** - For natural language processing using Titan embedding model and Claude LLM
- **Amazon Rekognition** - For content moderation of user-uploaded images
- **Amazon Textract** - For extracting text from menu images and signs

#### Workshop overview

In this workshop, you will learn how to build and deploy MapVibe, a full-stack application using:

- **Monorepo Architecture** - Using TurboRepo and Bun for efficient development
- **Frontend Applications**:
  - `apps/web` - Main user-facing web application (React 19, Vite, TailwindCSS)
  - `apps/admin` - Admin dashboard for content management
- **Backend Services**:
  - `apps/api` - Main API Lambda function handling REST endpoints
  - Multiple specialized Lambda functions for embeddings, RAG, OCR, Rekognition, and review aggregation
- **Infrastructure**:
  - Terraform modules for AWS services (VPC, RDS, Lambda, API Gateway, CloudFront, Cognito, etc.)
  - Infrastructure as Code approach for reproducible deployments

#### Architecture Overview

The MapVibe architecture follows a serverless-first approach:

1. **Frontend**: React applications deployed to S3 and served via CloudFront CDN
2. **API Layer**: API Gateway routes requests to Lambda functions
3. **Data Layer**: PostgreSQL RDS database for structured data storage
4. **AI Services**: Bedrock for embeddings and LLM, Rekognition for image analysis
5. **Storage**: S3 buckets for photos and static assets
6. **Authentication**: AWS Cognito for user management
7. **Security**: WAF for protection, Route53 and ACM for custom domains

![overview](/images/5-Workshop/4N1D-Architechture.drawio.png)
