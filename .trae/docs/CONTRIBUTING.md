---
title: "CONTRIBUTING.md"
purpose: "Defines development guidelines for contributing to the MVP codebase."
llm_guidance:
  - Enforce consistent coding, messaging, and documentation standards.
  - Ensure all contributions stay within scope.
context_level: "team"
allowed_changes:
  - Adding coding examples
forbidden_changes:
  - Introducing advanced branching strategies
---

# 📖 CONTRIBUTING - MVP
## Just: Keep It Simple

### Code Style
```typescript
// ✅ Types
interface Portfolio {
  holdings: Token[];
  totalValue: number;
}

// ✅ Error handling
try {
  const data = await api.get(...);
} catch (error) {
  console.error(error);
}

// ✅ Comments only for why, not what
// Calculate top 3 concentration (needed for risk score)
const top3 = holdings.sort(...).slice(0, 3);
```

### Git
```bash
# Small commits
git commit -m "feat: add portfolio table"
git commit -m "fix: portfolio calculation"

# One feature per commit
```

### PR Description
```
What: Added TokenTable component
Why: Users need to see individual holdings
How: Fetched from store, rendered with Tailwind
```

---