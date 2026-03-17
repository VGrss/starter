# Architecture

This document explains **why** the project is built the way it is. For setup and commands, see README.md. For design decisions, see DESIGN.md.

## Project Structure

```
src/
├── app/              # Next.js app router pages and layouts
├── components/
│   ├── ui/           # Primitives (shadcn, don't edit directly)
│   └── shared/       # Reusable project components
├── hooks/            # Custom React hooks
├── lib/              # Utilities, clients, shared logic
├── db/               # Database schema, migrations, queries
├── actions/          # Server actions
└── types/            # Shared TypeScript types
```

## Design Decisions

> Update this section as you make architectural choices. Each entry should explain **why**, not just what.

### Why [framework/tool]
<!-- e.g., Why Next.js App Router, Why Supabase, Why Tailwind -->
_To be filled as the stack is chosen._

### Data Flow
<!-- How data moves: user action → server action/API → DB → response → UI update -->
_To be filled as features are built._

### State Management
<!-- What lives in URL params, what in React state, what in server components -->
_To be filled as patterns emerge._

### Authentication
<!-- Auth strategy and why -->
_To be filled when auth is implemented._

### Error Handling Strategy
<!-- How errors flow: server actions return { success, error }, API routes use Response.json, client uses try/catch + toast -->
_To be filled as the pattern is established._

## What's Intentionally Not Here

> Document conscious omissions so future contributors don't re-add them.

_To be filled as decisions are made._

## Key Tradeoffs

> When you make a tradeoff (speed vs correctness, simplicity vs flexibility), document it here so future-you remembers the reasoning.

_To be filled as tradeoffs are made._
