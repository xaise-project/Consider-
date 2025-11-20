---
title: "DEPLOYMENT.md"
purpose: "Explains deployment pipeline for the MVP: Vercel, Railway, Supabase, Cloudflare."
llm_guidance:
  - Keep deployment lightweight and scalable.
  - Do not add workers, CRON jobs, or multi-region systems.
  - Use zero over-engineering.
context_level: "infra"
allowed_changes:
  - Environment variable clarifications
forbidden_changes:
  - Introducing Celery/Redis
  - K8s/docker orchestrations
---

# 🚀 DEPLOYMENT - MVP
## Simple 3-Step Deploy

## Step 1: Frontend (Vercel)

```bash
# 1. Push to GitHub
# 2. Vercel automatically builds & deploys
# 3. Done. Live at vercel.app

Env vars:
  VITE_API_URL=https://api.cryptotrack.app
```

## Step 2: Backend (Railway)

```bash
# 1. Push to GitHub
# 2. Railway builds & deploys
# 3. Done. Live at railway.app

Env vars:
  SUPABASE_URL=...
  SUPABASE_KEY=...
  MORALIS_API_KEY=...
  ALCHEMY_API_KEY=...
```

## Step 3: Database (Supabase)

```bash
# 1. Create free Supabase project
# 2. Run SQL (create 3 tables)
# 3. Done. That's it.
```

No: Docker, Kubernetes, load balancers, staging environments.

---
