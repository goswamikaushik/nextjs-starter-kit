# Next.js Boilerplate — Antigravity / Gemini Context

> **Read [CLAUDE.md](CLAUDE.md) first.** It is the single source of truth for this repo.

---

## Summary for Antigravity agents

Next.js 16.2.4 + React 19 frontend boilerplate (App Router, TypeScript strict, Tailwind v4, Redux Toolkit). Dev server runs on port 3000. This Next.js version has breaking changes — middleware is `src/proxy.ts`, not `middleware.ts`.

Full context in [CLAUDE.md](CLAUDE.md) including:

- **Middleware is `src/proxy.ts`** — creating `middleware.ts` is silently ignored
- **Redux store is scaffolded but empty** — all slices commented out
- **Auth forms are UI-only** — no submit handlers, no backend integration
- **React Compiler enabled** — no `useMemo`/`useCallback`/`React.memo`
- **All routes via `SITE_ROUTES`** in `src/constants/index.ts`

---

## Autonomy guidance

### Requires human review BEFORE executing

- Changes to `src/proxy.ts` (middleware)
- Adding env vars (requires Zod schema + deployment config update)
- Changing Redux persist config
- Modifying `SITE_ROUTES`
- Provider nesting changes in `src/app/(app)/layout.tsx`

### Safe for autonomous execution

- New chart components following existing patterns
- New pages following thin-shell + feature-component pattern
- Styling changes
- Adding Redux slices
- Narrow bug fixes

---

## Workflow

```bash
pnpm check-types   # TypeScript type check
pnpm lint          # ESLint
pnpm build         # Full production build
```

---

## Manual command rule

**NEVER run code generation, schema pulls, type generation, migrations, or any build step the developer should control. Stop and tell the user the exact command to run.**

- Add shadcn component: `pnpm dlx shadcn@latest add <component>`
- Type-check: `pnpm check-types`
