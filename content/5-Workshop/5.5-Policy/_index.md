---
title : "Development & Deployment"
date: 2025-09-09
weight : 5
chapter : false
pre : " <b> 5.5. </b> "

---

#### Overview

This section covers the development workflow and deployment process for MapVibe applications.

#### Development Workflow

1. **Local Development**
   - Run frontend apps locally with `bun run dev`
   - Test API locally with `bun run dev` in `apps/api`
   - Use local database or connect to dev RDS

2. **Build Process**
   - Build all packages: `bun run build`
   - Build specific app: `cd apps/web && bun run build`

3. **Testing**
   - Type checking: `bun run type-check`
   - Linting: `bun run lint`

#### Deployment Process

##### Deploy Infrastructure

```bash
cd infrastructure/terraform
terraform apply
```

##### Deploy API

```bash
# Build API
cd apps/api
bun run build

# Deploy using script
bun run deploy
# Or use: pwsh ../../scripts/deploy-api.ps1
```

##### Deploy Frontend (Web)

```bash
# Build frontend
cd apps/web
bun run build

# Deploy to S3 + CloudFront
bun run deploy
```

##### Deploy Admin Dashboard

```bash
# Build admin
cd apps/admin
bun run build

# Deploy using script
pwsh ../../scripts/deploy-admin.ps1
```

##### Run Database Migrations

```bash
pwsh scripts/deploy-migrate.ps1
```

#### Deployment Scripts

The `scripts/` directory contains PowerShell scripts for deployment:
- `deploy-api.ps1` - Deploy API Lambda
- `deploy-admin.ps1` - Deploy admin dashboard
- `deploy-migrate.ps1` - Run database migrations
- `build-all-lambdas.ps1` - Build all Lambda functions

#### Best Practices

1. **Always test locally** before deploying
2. **Use environment-specific configurations**
3. **Monitor CloudWatch logs** after deployment
4. **Verify deployments** by testing endpoints
5. **Keep infrastructure in sync** with code changes

