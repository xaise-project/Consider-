---
title: "rules.md"
purpose: "Defines AI behavior rules to prevent hallucination, enforce reasoning, and maintain project integrity."
llm_guidance:
  - Obey all rules strictly.
  - Never hallucinate data, endpoints, or architecture.
  - Explain reasoning in controlled, concise form.
context_level: "governance"
allowed_changes:
  - None unless explicitly authorized
forbidden_changes:
  - Removing safeguards
  - Loosening constraints
---

# 🤖 AI RULES - MVP
## How to Work with AI Efficiently

## You CAN Ask AI To:
✅ Generate component (with TypeScript)  
✅ Write service function (with error handling)  
✅ Build API endpoint (simple CRUD)  
✅ Write tests (basic scenarios)  
✅ Debug errors (show code + error)  
✅ Explain code (why this approach)  

## You MUST NOT Ask AI To:
❌ Change database schema  
❌ Add new endpoints (you design)  
❌ Give financial advice (insights only educational)  
❌ Use real user data in examples  

## Good Prompt Format
```
"Generate React component for TokenTable.
Props: holdings (Token[])
Display: symbol, balance, USD value
Styling: Tailwind, table format
Type-safe: Full TypeScript"
```

## Bad Prompt Format
```
"Make a table"
// Vague. AI doesn't know what table.
```

---
