# Project Name

<!-- Brief one-liner: what this project does -->

---

## Accounts & Profiles

<!-- Fill in so Claude knows which accounts/orgs to use for git, deploy, APIs, etc. -->

| Service | Handle / Org | Notes |
|---------|-------------|-------|
| GitHub | <!-- e.g. VGrss --> | <!-- default org, SSH vs HTTPS --> |
| Vercel | <!-- team or personal --> | <!-- project linking conventions --> |
| Deployment | <!-- e.g. Vercel, Netlify, Fly.io --> | <!-- production URL, staging URL --> |
| Database | <!-- e.g. Supabase, Neon, PlanetScale --> | <!-- connection method, env var name --> |
| Email | <!-- e.g. Resend, Postmark --> | <!-- sending domain --> |
| AI/LLM | <!-- e.g. Anthropic, OpenAI --> | <!-- which models, gateway --> |

<!-- Add or remove rows as needed. Keep secrets in .env, only context here. -->

---

## UI Design Philosophy

### Core Identity

<!-- Describe the visual identity in 1-2 sentences. What's the inspiration? What feeling should it evoke? -->

### Color Palette

<!-- Define semantic color tokens. Always use token names, never raw hex. -->

| Token | Hex | Tailwind | Usage |
|-------|-----|----------|-------|
| | | | |

### Typography

<!-- Define font families, loading method, and usage rules -->

| Variable | Tailwind class | Font | Usage |
|----------|---------------|------|-------|
| | | | Headings |
| | | | Body text, UI |

### Theme Configuration

<!-- How is the design system configured? (Tailwind config, CSS variables, @theme, etc.) -->

### Design Principles

<!-- List 2-4 core design pillars. For each: name, description, and a practical rule. -->

### Animation Philosophy

<!-- Define animation conventions: entrance style, timing, easing, what to avoid. -->

### Component Patterns

<!-- Define patterns for cards, buttons, status indicators, and other recurring UI elements. -->

### Responsive Design

<!-- Define breakpoints, container strategy, and mobile-specific rules. -->

| Breakpoint | Prefix | Usage |
|-----------|--------|-------|
| Default | (none) | Mobile |
| `md` | `md:` | Tablet |
| `lg` | `lg:` | Desktop |

### Copywriting Voice

<!-- Define tone, style, and specific do/don't rules for copy. -->

| Trait | Description |
|-------|-------------|
| | |

---

## Project Guidelines

### Tech Stack

| Tool | Version | Docs |
|------|---------|------|
| | | |

### Project Structure

<!-- Define the folder structure. Keep it as a code block for clarity. -->

```
src/
├── app/
├── components/
│   ├── ui/           # Primitives (don't edit)
│   └── shared/       # Reusable components
├── hooks/
├── lib/
├── db/
├── actions/
└── types/
```

### Naming Conventions

| Item | Convention | Example |
|------|-----------|---------|
| Files/folders | `kebab-case` | `user-profile.tsx` |
| Components | `PascalCase` named export | `export function UserProfile()` |
| Pages | Default export | `export default function Page()` |
| Hooks | `camelCase` with `use` prefix | `useAuth()` |
| Server Actions | `camelCase` verb-first | `createUser()` |
| Types | `PascalCase` | `type UserProfile = ...` |

### Environment Variables

See `.env.example` for the full list. Copy it to start:

```bash
cp .env.example .env
```

<!-- Describe what each var is for. Keep actual values in .env only. -->

### Database

<!-- ORM, connection method, migration workflow, type inference rules. -->

### Authentication

<!-- Auth library, key files, setup commands. -->

### External Services

<!-- List integrations, singleton patterns, server-side-only rules. -->

### API Response Convention

<!-- Define the standard response shape for success and error cases. -->

```typescript
// Success
return Response.json({ data: T }, { status: 200 });

// Error
return Response.json({ error: "message", code: "ERROR_CODE" }, { status: 4xx });
```

### Error Handling

| Context | Pattern |
|---------|---------|
| Server Actions | Return `{ success: false, error }` or throw |
| API routes | `Response.json({ error })` with status code |
| Client mutations | `try/catch`, show toast |
| External APIs | `try/catch`, log server-side, return user-friendly error |

### State Management

<!-- Define where state lives: server components, URL params, client state, auth state. -->

### Shared Components

<!-- Catalog reusable components. Update this as new ones are created. -->

| Component | Location | Usage |
|-----------|----------|-------|
| | | |

### Conventions

<!-- List short, concrete rules that apply project-wide. -->

### Testing

<!-- Define test framework, file naming, and strategy. -->

### Git Conventions

- Branch names: `feat/short-description`, `fix/short-description`, `chore/short-description`
- Commit messages: imperative mood, lowercase, no period
- One logical change per commit

### Local Development

<!-- Commands to start the dev environment. List all services that must be running. -->

```bash
# Start dev server
```

### Do NOT

<!-- Explicit anti-patterns. Add items as you discover them during the project. -->

- Use `any` types
- Use inline styles instead of design tokens
- Leave `console.log` in committed code
- Skip error handling on external APIs
- Create files longer than 500 lines
