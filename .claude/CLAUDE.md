# CLAUDE.md - trpc-template

## Project
Full-Stack TypeScript: React 19 + tRPC 11 + Express + Drizzle ORM + MySQL

## Engineering Standards (Staff/Principal Level)

### Decision Making
- 95%+ confidence required before making changes. When unsure, investigate first.
- Always verify against official documentation. Do not guess.
- Double check changes won't break existing functionality.

### Principles
- **SOLID**: Apply pragmatically, not dogmatically.
- **KISS**: Simplest solution that works. No premature abstraction.
- **DRY**: Extract at 3+ repetitions only. Premature DRY is worse than repetition.
- **YAGNI**: Don't build for hypothetical future requirements.

### Code Quality
- Meaningful names, small functions, no dead code, no commented-out code.
- Fail fast: validate at boundaries, return early, max 3 levels nesting.
- Immutability by default. Mutate only when necessary.
- Changes must be reviewable in under 15 minutes. Split large changes.

### Testing
- Unit tests for logic, integration tests for boundaries, skip trivial code.
- Run tests after every change. If no test suite exists, verify manually.

### Security
- Never commit secrets or .env files.
- Validate all user input at system boundaries.
- Use parameterized queries, never string concatenation for SQL.
- Keep dependencies updated.

### Git
- Single-line commit messages: `type(scope): description`
- Types: feat, fix, docs, style, refactor, test, chore
- No co-author references. No emojis.

### Documentation
- No markdown files without explicit approval.
- Comment only when logic is not obvious.
- Public API functions should have docstrings.

## Full-Stack tRPC Best Practices

### Architecture
- Monorepo with pnpm workspaces.
- tRPC for type-safe API layer (no REST endpoints).
- Drizzle ORM for database access (type-safe, no raw SQL).
- Zod schemas shared between client and server.

### Backend
- Express adapter for tRPC server.
- Input validation via Zod at router level.
- Use middleware for auth, logging.
- Database migrations via drizzle-kit.

### Frontend
- React Query (via tRPC) for server state.
- Optimistic updates for better UX.
- Error boundaries at route level.
- Tailwind CSS for styling.

### Type Safety
- Strict TypeScript (`strict: true`).
- No `any` types. Use `unknown` and narrow.
- Infer types from tRPC routers, Drizzle schemas.
- Shared types between client and server via tRPC.

### Build
- pnpm for package management.
- Turbo or tsx for development.
- Single Docker image for full-stack app.
