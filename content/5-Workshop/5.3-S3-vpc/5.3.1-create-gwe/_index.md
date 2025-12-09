---
title : "Monorepo Setup"
date: 2025-09-09
weight : 1
chapter : false
pre : " <b> 5.3.1 </b> "

---

#### Clone the Repository

First, clone the MapVibe repository:

```bash
git clone <repository-url>
cd mapvibe
```

#### Install Dependencies

Install all dependencies using Bun:

```bash
bun install
```

This will install dependencies for all workspaces in the monorepo.

#### Workspace Configuration

The project uses Bun workspaces defined in `package.json`:

```json
{
  "workspaces": [
    "apps/*",
    "packages/*",
    "infrastructure"
  ]
}
```

#### TurboRepo Configuration

TurboRepo is configured in `turbo.json` to manage build pipelines:

- **build** - Builds all packages and apps
- **dev** - Runs development servers
- **lint** - Lints all code
- **type-check** - Type checks TypeScript
- **deploy** - Deploys applications

#### Development Scripts

Common scripts available at the root:

```bash
# Start all development servers
bun run dev

# Build all packages and apps
bun run build

# Lint all code
bun run lint

# Type check
bun run type-check

# Format code
bun run format
```

#### Environment Variables

Create `.env` files as needed:

1. Root `.env` - For infrastructure variables
2. `apps/web/.env` - For frontend configuration
3. `apps/admin/.env` - For admin dashboard

Contact the project maintainer for required environment variables.

#### Verify Setup

Verify your setup by running:

```bash
# Check Bun version
bun --version

# Install dependencies
bun install

# Run type check
bun run type-check
```

If all commands succeed, your monorepo is ready for development!
