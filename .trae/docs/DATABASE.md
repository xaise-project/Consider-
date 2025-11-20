---
title: "DATABASE.md"
purpose: "Defines Supabase/PostgreSQL schema for MVP data storage."
llm_guidance:
  - Always use only tables defined here.
  - Schema expansion must be requested explicitly by the user.
  - Maintain normalization and MVP constraints.
context_level: "storage"
allowed_changes:
  - Column clarifications
forbidden_changes:
  - Adding historical OHLC tables
  - Creating analytics-heavy datasets
---

# 💾 DATABASE - MVP
## Minimal Schema

```sql
-- users
CREATE TABLE users (
  id UUID PRIMARY KEY,
  wallet_address VARCHAR(42) UNIQUE,
  created_at TIMESTAMP
);

-- portfolios
CREATE TABLE portfolios (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  raw_data JSONB,                    -- Raw token list from Moralis
  total_usd_value DECIMAL(18, 2),
  last_updated TIMESTAMP
);

-- insights
CREATE TABLE insights (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  type VARCHAR(50),                  -- 'concentration', 'diversification', etc
  title VARCHAR(255),
  content TEXT,
  created_at TIMESTAMP
);
```

No: RLS policies, advanced triggers, audit logs.  
Yes: Simple queries. Basic foreign keys.

---
