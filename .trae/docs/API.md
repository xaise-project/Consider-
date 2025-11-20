---
title: "API.md"
purpose: "Defines FastAPI endpoints and expected request/response models for the MVP."
llm_guidance:
  - Only reference endpoints defined here.
  - Never propose new routes unless explicitly asked.
  - Keep responses deterministic and aligned with backend logic.
context_level: "interface"
allowed_changes:
  - Schema clarification
  - Type annotations
forbidden_changes:
  - Adding async complexity
  - Introducing scheduling/cron endpoints
---

# 🔌 API SPECIFICATION - MVP
## 3 Endpoints. That's It.

## Base Info
- **URL:** `https://api.cryptotrack.app`
- **Auth:** JWT token (simple)
- **Rate Limit:** None for MVP

---

## Endpoint 1: POST /portfolio/raw

```
Purpose: User submits wallet address + holdings

Request:
{
  "address": "0x742d35Cc...",
  "tokens": [
    { "symbol": "BTC", "balance": "0.5", "chainId": 1 },
    { "symbol": "ETH", "balance": "10", "chainId": 1 }
  ]
}

Response (200):
{
  "status": "ok",
  "portfolio_id": "uuid-123"
}

Error (400):
{
  "error": "Invalid token format"
}
```

---

## Endpoint 2: GET /portfolio/analysis

```
Purpose: Return calculated portfolio metrics

Response (200):
{
  "health_score": 74,
  "risk_score": 68,
  "diversification_score": 72,
  "concentration": { "top_3_percent": 83 },
  "total_usd_value": 127345.82
}

That's it. No advanced metrics. No ML predictions.
```

---

## Endpoint 3: GET /insights

```
Purpose: Return pre-calculated insight cards

Response (200):
{
  "insights": [
    {
      "type": "concentration",
      "title": "High Concentration Risk",
      "content": "Your top 3 assets are 83% of portfolio...",
      "severity": "high",
      "confidence": 0.92
    },
    {
      "type": "diversification",
      "title": "Limited Sector Coverage",
      "content": "Only L1 blockchains. No DeFi or Layer 2...",
      "severity": "medium"
    }
  ]
}

Pre-written templates (no AI). Just match portfolio against rules.
```

---