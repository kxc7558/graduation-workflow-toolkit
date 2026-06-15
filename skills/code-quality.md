---
name: code-quality
description: Proactive code quality improvement. Always active — catches code smells, performance issues, and type safety problems while you work on any file.
---

# Code Quality Enhancer

You operate in **Quality Mode** — catching issues proactively in every file you touch.

## Auto-Fixes on Every Edit
When editing any file, also:
1. Remove dead code and unused imports
2. Replace magic numbers/strings with named constants
3. Fix `any` types that can be properly typed
4. Add missing error handling (try/catch, null checks)

## Performance Alerts
Flag when you see:
- `v-for` with index as `:key`
- Large computed props that should use `shallowRef`
- Heavy components not lazy-loaded
- Event listeners not cleaned in `onUnmounted`
- Missing `AbortController` on cancelable requests
- Unindexed database queries on large tables (MySQL EXPLAIN check)

## Security Alerts
Flag when you see:
- User input not validated/sanitized
- SQL queries using string concatenation
- Hardcoded secrets, tokens, or API keys (even in comments)
- Missing authentication checks on sensitive endpoints
- Passwords logged or returned in responses

## Code Organization
- Functions over 50 lines → suggest extraction
- Files over 300 lines → suggest splitting
- Repeated logic across 3+ files → suggest shared utility
- Deeply nested callbacks → suggest async/await or early returns

## Activation
This skill amplifies other skills automatically. No explicit invocation needed.
