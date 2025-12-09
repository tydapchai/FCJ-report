---
title : "Application Details"
date: 2025-09-09
weight : 2
chapter : false
pre : " <b> 5.3.2 </b> "

---

#### Frontend Applications

##### Web Application (`apps/web`)

The main user-facing application built with:
- **React 19** - Latest React with concurrent features
- **Vite** - Fast build tool and dev server
- **TailwindCSS** - Utility-first CSS framework
- **React Router** - Client-side routing
- **TanStack Query** - Data fetching and caching
- **TipTap** - Rich text editor for reviews

**Key Features:**
- Natural language search using AI
- Place discovery and recommendations
- User reviews and ratings
- Photo uploads
- User profiles and saved places
- Responsive design for mobile and desktop

**Development:**
```bash
cd apps/web
bun run dev
```

**Build:**
```bash
bun run build
```

##### Admin Dashboard (`apps/admin`)

Admin interface for content management:
- **React 19** with Vite
- **TailwindCSS** for styling
- Admin-specific components and pages

**Key Features:**
- Content moderation
- User management
- Analytics dashboard
- Place approval workflow
- Review management

**Development:**
```bash
cd apps/admin
bun run dev
```

#### Backend API (`apps/api`)

Main API Lambda function handling:
- REST API endpoints
- Authentication with Cognito
- Database operations with Kysely
- S3 operations for photos
- Integration with AWS Bedrock
- SQS queue processing

**Key Handlers:**
- Places (CRUD, search, nearby)
- Reviews (create, vote, comment)
- Users (profile, photos, stats)
- Photos (upload, delete)
- Activities (tracking)

**Development:**
```bash
cd apps/api
bun run dev
```

**Build:**
```bash
bun run build
```

#### Lambda Functions

Specialized Lambda functions in infrastructure:

1. **lambda-embeddings** - Generates embeddings for places using Bedrock
2. **lambda-rag** - Retrieval Augmented Generation for AI search
3. **lambda-ocr-menu** - Extracts text from menu images using Textract
4. **lambda-rekognition** - Content moderation using Rekognition
5. **lambda-review-aggregate** - Aggregates review statistics
6. **lambda-s3-trigger** - Processes S3 upload events
7. **lambda-migration** - Database migration runner

#### Shared Packages

- **types** - TypeScript definitions shared across apps
- **ui-components** - Reusable React components
- **database** - Kysely-based database layer
- **utils** - Common utility functions
- **constants** - Application constants
