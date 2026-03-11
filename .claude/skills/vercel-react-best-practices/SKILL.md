---
name: vercel-react-best-practices
description: Comprehensive performance optimization guide for React and Next.js applications, maintained by Vercel. Contains 58 rules across 8 categories, prioritized by impact to guide automated refactoring and code generation.
---

# Vercel React Best Practices

Comprehensive performance optimization guide for React and Next.js applications, maintained by Vercel. Contains 58 rules across 8 categories, prioritized by impact to guide automated refactoring and code generation.

## When to Apply

Reference these guidelines when:

- Optimizing bundle size or load times
- Refactoring existing React/Next.js code
- Reviewing code for performance issues
- Implementing data fetching (client or server-side)
- Writing new React components or Next.js pages

## Rule Categories by Priority

| Priority | Category | Impact | Prefix |
| --- | --- | --- | --- |
| 1 | Eliminating Waterfalls | CRITICAL | `async-` |
| 2 | Bundle Size Optimization | CRITICAL | `bundle-` |
| 3 | Server-Side Performance | HIGH | `server-` |
| 4 | Client-Side Data Fetching | MEDIUM-HIGH | `client-` |
| 5 | Re-render Optimization | MEDIUM | `rerender-` |
| 6 | Rendering Performance | MEDIUM | `rendering-` |
| 7 | JavaScript Performance | LOW-MEDIUM | `js-` |
| 8 | Advanced Patterns | LOW | `advanced-` |

## Quick Reference

### 1. Eliminating Waterfalls (CRITICAL)

- `async-suspense-boundaries` - Use Suspense to stream content
- `async-api-routes` - Start promises early, await late in API routes
- `async-dependencies` - Use better-all for partial dependencies
- `async-parallel` - Use `Promise.all()` for independent operations
- `async-defer-await` - Move `await` into branches where actually used

### 2. Bundle Size Optimization (CRITICAL)

- `bundle-preload` - Preload on hover/focus for perceived speed
- `bundle-conditional` - Load modules only when feature is activated
- `bundle-defer-third-party` - Load analytics/logging after hydration
- `bundle-dynamic-imports` - Use `next/dynamic` for heavy components
- `bundle-barrel-imports` - Import directly, avoid barrel files

### 3. Server-Side Performance (HIGH)

- `server-after-nonblocking` - Use `after()` for non-blocking operations
- `server-parallel-fetching` - Restructure components to parallelize fetches
- `server-serialization` - Minimize data passed to client components
- `server-hoist-static-io` - Hoist static I/O (fonts, logos) to module level
- `server-dedup-props` - Avoid duplicate serialization in RSC props
- `server-cache-lru` - Use LRU cache for cross-request caching
- `server-cache-react` - Use `React.cache()` for per-request deduplication
- `server-auth-actions` - Authenticate server actions like API routes

### 4. Client-Side Data Fetching (MEDIUM-HIGH)

- `client-localstorage-schema` - Version and minimize `localStorage` data
- `client-passive-event-listeners` - Use passive listeners for scroll
- `client-event-listeners` - Deduplicate global event listeners
- `client-swr-dedup` - Use SWR for automatic request deduplication

### 5. Re-render Optimization (MEDIUM)

- `rerender-use-ref-transient-values` - Use refs for transient frequent values
- `rerender-transitions` - Use `startTransition` for non-urgent updates
- `rerender-move-effect-to-event` - Put interaction logic in event handlers
- `rerender-simple-expression-in-memo` - Avoid memo for simple primitives
- `rerender-lazy-state-init` - Pass function to `useState` for expensive values
- `rerender-functional-setstate` - Use functional `setState` for stable callbacks
- `rerender-derived-state-no-effect` - Derive state during render, not effects
- `rerender-derived-state` - Subscribe to derived booleans, not raw values
- `rerender-dependencies` - Use primitive dependencies in effects
- `rerender-memo-with-default-value` - Hoist default non-primitive props
- `rerender-memo` - Extract expensive work into memoized components
- `rerender-defer-reads` - Don't subscribe to state only used in callbacks

### 6. Rendering Performance (MEDIUM)

- `rendering-usetransition-loading` - Prefer `useTransition` for loading state
- `rendering-conditional-render` - Use ternary, not `&&` for conditionals
- `rendering-activity` - Use Activity component for show/hide
- `rendering-hydration-suppress-warning` - Suppress expected mismatches
- `rendering-hydration-no-flicker` - Use inline script for client-only data
- `rendering-svg-precision` - Reduce SVG coordinate precision
- `rendering-hoist-jsx` - Extract static JSX outside components
- `rendering-content-visibility` - Use `content-visibility` for long lists
- `rendering-animate-svg-wrapper` - Animate `div` wrapper, not SVG element

### 7. JavaScript Performance (LOW-MEDIUM)

- `js-tosorted-immutable` - Use `toSorted()` for immutability
- `js-set-map-lookups` - Use `Set`/`Map` for O(1) lookups
- `js-min-max-loop` - Use loop for min/max instead of sort
- `js-hoist-regexp` - Hoist `RegExp` creation outside loops
- `js-early-exit` - Return early from functions
- `js-length-check-first` - Check array length before expensive comparison
- `js-combine-iterations` - Combine multiple `filter`/`map` into one loop
- `js-cache-storage` - Cache `localStorage`/`sessionStorage` reads
- `js-cache-function-results` - Cache function results in module-level `Map`
- `js-cache-property-access` - Cache object properties in loops
- `js-index-maps` - Build `Map` for repeated lookups
- `js-batch-dom-css` - Group CSS changes via classes or `cssText`

### 8. Advanced Patterns (LOW)

- `advanced-use-latest` - `useLatest` for stable callback refs
- `advanced-init-once` - Initialize app once per app load
- `advanced-event-handler-refs` - Store event handlers in refs

## How to Use

Read individual rule files for detailed explanations and code examples:

```text
rules/async-parallel.md
rules/bundle-barrel-imports.md
```

Each rule file contains:

- Additional context and references
- Correct code example with explanation
- Incorrect code example with explanation
- Brief explanation of why it matters

## Full Compiled Document

For the complete guide with all rules expanded: `AGENTS.md`

