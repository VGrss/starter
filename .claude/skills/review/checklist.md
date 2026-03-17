# Pre-Landing Review Checklist

## Instructions

Review the `git diff <base>...HEAD` output for the issues listed below. Be specific — cite `file:line` and suggest fixes. Skip anything that's fine. Only flag real problems.

**Two-pass review:**
- **Pass 1 (CRITICAL):** Highest severity. Run these first.
- **Pass 2 (INFORMATIONAL):** Lower severity but still actioned.

**Output format:**

```
Pre-Landing Review: N issues (X critical, Y informational)

**AUTO-FIXED:**
- [file:line] Problem → fix applied

**NEEDS INPUT:**
- [file:line] Problem description
  Recommended fix: suggested fix
```

If no issues found: `Pre-Landing Review: No issues found.`

---

## Pass 1 — CRITICAL

### SQL & Data Safety
- String interpolation in SQL — always use parameterized queries
- Check-then-set patterns that should be atomic (TOCTOU races)
- Bypassing ORM validations on fields that have constraints
- N+1 queries: missing `.includes()` / eager loading for associations used in loops

### Race Conditions & Concurrency
- Read-check-write without uniqueness constraint or conflict handling
- `findOrCreate` on columns without unique DB index — concurrent calls create duplicates
- Status transitions without atomic WHERE old_status = ? UPDATE SET new_status
- Double-submit potential on forms without debouncing or idempotency keys

### Security & Trust Boundaries
- `dangerouslySetInnerHTML` or equivalent on user-controlled data (XSS)
- LLM-generated values written to DB without format validation
- Missing auth checks on API routes
- Secrets or tokens compared with `===` instead of constant-time comparison
- `any` types on API boundaries that bypass validation

### Enum & Value Completeness
When the diff introduces a new enum value, status string, or type constant:
- Trace it through every consumer. Read each file that switches on or filters by that value.
- Check allowlists/filter arrays containing sibling values
- Check `switch`/`if-else` chains — does the new value fall through to a wrong default?

---

## Pass 2 — INFORMATIONAL

### Conditional Side Effects
- Code paths that branch on a condition but forget to apply a side effect on one branch
- Log messages that claim an action happened but the action was conditionally skipped

### Dead Code & Consistency
- Variables assigned but never read
- Imports that are no longer used
- Comments/docstrings that describe old behavior after the code changed

### Test Gaps
- New functionality without corresponding tests
- Negative-path tests that assert type/status but not side effects
- Security enforcement features without integration tests

### Type Safety
- `any` types that could be narrowed
- Type assertions (`as X`) that mask real type mismatches
- Missing null checks on optional values used without `?.`

### Performance
- O(n*m) lookups in loops (Array.find inside a loop instead of Map/Set)
- Inline `<style>` blocks in components (re-parsed every render)
- Missing `key` props in list renders
- Unbounded queries without pagination or limits

### Error Handling
- `try/catch` that swallows errors silently (empty catch block)
- External API calls without error handling
- Missing loading/error states in UI for async operations
- Promises without `.catch()` or try/catch in async functions

---

## Fix-First Heuristic

```
AUTO-FIX (agent fixes without asking):     ASK (needs human judgment):
├─ Dead code / unused variables            ├─ Security (auth, XSS, injection)
├─ N+1 queries (missing eager loading)     ├─ Race conditions
├─ Stale comments contradicting code       ├─ Design decisions
├─ Missing error handling on APIs          ├─ Large fixes (>20 lines)
├─ Unused imports                          ├─ Enum completeness
├─ Variables assigned but never read       ├─ Removing functionality
└─ Obvious type narrowing                  └─ Anything changing user-visible behavior
```

**Rule of thumb:** If the fix is mechanical and a senior engineer would apply it without discussion, AUTO-FIX. If reasonable engineers could disagree, ASK.

---

## Suppressions — DO NOT flag these

- Redundancy that aids readability
- "Add a comment explaining why" — comments rot, code is truth
- "This assertion could be tighter" when it already covers the behavior
- Consistency-only changes with no functional impact
- Harmless no-ops
- Anything already addressed in the diff you're reviewing
