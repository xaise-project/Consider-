---
title: "FRONTEND.md"
purpose: "Defines React component architecture and UI behavior for the MVP."
llm_guidance:
  - Respect the minimalist UI structure.
  - Avoid adding charts, advanced analytics, or complex state machines.
  - Align components with backend capabilities.
context_level: "interface"
allowed_changes:
  - Component naming consistency
forbidden_changes:
  - New pages
  - Historical graphs
  - Benchmarking UI
---

# 🎨 FRONTEND - MVP
## Single Dashboard Page

```
/pages
  └─ Dashboard.tsx
     └─ Fetch portfolio → display

/components
  ├─ PortfolioHeader.tsx    (Total value + date)
  ├─ QuickStats.tsx         (3 cards: Health, Risk, Div)
  ├─ TokenTable.tsx         (Holdings list)
  └─ InsightCard.tsx        (Individual insight)

/store
  ├─ walletStore.ts        (address, connected)
  └─ portfolioStore.ts     (holdings, scores, insights)

/services
  ├─ api.ts                (HTTP client)
  └─ portfolioService.ts   (fetch → store updates)
```

**Pattern:** Component needs data → calls service → service fetches + updates store → component re-renders.

---
