---
title: "TROUBLESHOOTING.md"
purpose: "Lists MVP-level common issues and resolutions."
llm_guidance:
  - Follow troubleshooting steps exactly as defined.
  - When helping, remain aligned with MVP architecture.
context_level: "support"
allowed_changes:
  - Add real errors encountered during development
forbidden_changes:
  - Adding advanced issues from non-MVP systems
---

# 🔧 TROUBLESHOOTING - MVP
## Only What Will Likely Break

### WalletConnect Not Working

**Problem:** "Provider not found"

**Fix:**
```typescript
// Check: RPC endpoint is correct
const config = getDefaultConfig({
  chains: [mainnet, polygon],
  // Make sure chain is in list
});

// If still broken: Try MetaMask directly
// WalletConnect uses relay service (sometimes slow)
```

---

### Moralis Returns Empty

**Problem:** Balance shows as 0

**Fix:**
```python
# Make sure wallet has tokens on that chain
# Moralis might be slow → retry in 5 seconds
# Check: Is chain ID correct? (1 for Ethereum, 137 for Polygon)
```

---

### Supabase Query Fails

**Problem:** 401 Unauthorized

**Fix:**
```python
# Check: JWT token is valid
# Check: User exists in users table
# For MVP: No RLS yet. Query should work if user exists.
```

---
