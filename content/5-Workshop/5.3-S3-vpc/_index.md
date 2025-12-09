---
title : "Project Structure"
date: 2025-09-09
weight : 3
chapter : false
pre : " <b> 5.3. </b> "

---

#### Monorepo Architecture

MapVibe uses a **monorepo** architecture managed by **TurboRepo** and **Bun**. This allows for:
- Shared code and dependencies across multiple applications
- Efficient builds with caching
- Consistent tooling and configurations
- Simplified dependency management

#### Directory Structure

```
mapvibe/
├── apps/                    # Applications
│   ├── web/                 # Main frontend application
│   ├── admin/               # Admin dashboard
│   └── api/                 # Backend API Lambda function
├── packages/                # Shared packages
│   ├── types/               # TypeScript type definitions
│   ├── ui-components/       # Shared React components
│   ├── database/            # Database layer (Kysely)
│   ├── api-functions/       # Shared API utilities
│   ├── utils/               # Common utilities
│   └── constants/           # Shared constants
├── infrastructure/          # Infrastructure as Code
│   ├── terraform/           # Terraform configurations
│   │   ├── main.tf          # Main configuration
│   │   └── modules/         # Terraform modules
│   └── s3-cloudfront/       # S3 and CloudFront configs
├── scripts/                 # Deployment and build scripts
├── package.json             # Root package configuration
├── turbo.json               # TurboRepo configuration
└── tsconfig.json            # TypeScript configuration
```

#### Applications

1. **`apps/web`** - Main user-facing web application
   - Built with React 19, Vite, and TailwindCSS
   - Features: Search, place discovery, reviews, user profiles
   - Deployed to S3 + CloudFront

2. **`apps/admin`** - Admin dashboard
   - Built with React 19, Vite, and TailwindCSS
   - Features: Content moderation, analytics, user management
   - Deployed to separate S3 + CloudFront

3. **`apps/api`** - Main API Lambda function
   - Handles REST API endpoints
   - Integrates with RDS, S3, Cognito, Bedrock
   - Built with TypeScript and Node.js

#### Shared Packages

- **`packages/types`** - Shared TypeScript types and interfaces
- **`packages/ui-components`** - Reusable React UI components
- **`packages/database`** - Database access layer using Kysely
- **`packages/utils`** - Common utility functions
- **`packages/constants`** - Application constants

#### Infrastructure

The `infrastructure/` directory contains Terraform modules for:
- VPC and networking
- RDS PostgreSQL database
- Lambda functions (API, embeddings, RAG, OCR, Rekognition, etc.)
- API Gateway
- CloudFront and S3
- Cognito User Pool
- Route53 and ACM
- WAF

#### Content

- [Monorepo Setup](5.3.1-create-gwe/)
- [Application Details](5.3.2-test-gwe/)
