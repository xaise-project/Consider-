---
title: "ARCHITECTURE.md"
purpose: "Defines MVP system architecture for Consider AI Insights Module."
llm_guidance:
  - Follow the defined architecture strictly.
  - Do not introduce new components unless user requests expansion.
  - Prioritize simplicity, clarity, and MVP constraints.
  - All reasoning must stay aligned with this system design.
context_level: "system"
allowed_changes: 
  - Minor optimizations
  - Clarifications
forbidden_changes:
  - Adding new services
  - Introducing workers, schedulers, or pipelines
  - Over-engineering beyond MVP
---
# Consider- MVP Documentation
## Clean, Focused, Phase-Aware

**Document Version:** 1.0 MVP  
**Status:** Ready for Development  
**Phases:** 3 (MVP → Phase 2 → Phase 3)

---

# 📐 SYSTEM ARCHITECTURE - MVP
## Focus: Core Value Loop Only

## What CryptoTrack Does (MVP)

```
User connects wallet 
→ Shows portfolio balance 
→ Displays basic insights 
→ User makes decisions (no AI telling them what to do)
```

That's it. MVP = Display + Insights. Not complex.

---

## Simple Architecture Diagram

```
┌──────────────────────────────────┐
│       User's Browser             │
│  (React - ~100KB gzip)          │
└────────────┬─────────────────────┘
             │ HTTPS
┌────────────▼─────────────────────┐
│    Backend (FastAPI)             │
│  (Portfolio + Basic Scoring)     │
└────────────┬─────────────────────┘
             │ SQL
┌────────────▼─────────────────────┐
│    Supabase PostgreSQL           │
│  (users, portfolios, insights)   │
└──────────────────────────────────┘
             │
     ┌───────┴────────┬────────────┐
     │                │            │
  Moralis          Alchemy      CoinGecko
  (Balance)      (On-Chain)     (Pricing)
```

No: Real-time subscriptions, microservices, queue systems, LLM pipelines.  
Yes: Simple HTTP → fetch → store → display.

---

## Frontend Stack (MVP)

```
React 18 + TypeScript
Vite (build)
Tailwind (styling)
Zustand (state)

Structure:
/pages → Dashboard only (PortfolioHealth, RiskAnalysis = tabs, not pages)
/components → Reusable UI pieces
/store → Single source of truth
/services → API calls only
```

**Rule:** Components are dumb (display only). Services are smart (fetch + calculate).

---

## Backend Stack (MVP)

```
FastAPI + Python
3 simple routes:
  POST /portfolio/raw     (receive wallet data)
  GET /portfolio/analysis (calculate + return scores)
  GET /insights           (return pre-calculated insights)

No: Background jobs, cron tasks, message queues
Yes: Synchronous routes. Calculate on demand.
```

---

## Database (MVP)

```
3 tables:
  - users (id, wallet_address, created_at)
  - portfolios (id, user_id, raw_data, total_usd_value, last_updated)
  - insights (id, user_id, type, title, content, created_at)

No RLS yet. Single user per wallet. No row-level policies needed at MVP scale.
```

---

## Deployment (MVP)

```
Frontend: Vercel (push → deploy)
Backend: Railway (push → deploy)
Database: Supabase free tier
DNS: Cloudflare free tier

No staging. No load balancing. No containers. Direct push = live.
```

---