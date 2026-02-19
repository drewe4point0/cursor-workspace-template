# Project: [PROJECT NAME]

[One-line description]

---

## Compound Engineering

**Each unit of work should make subsequent work easier, not harder.**

```
Brainstorm → Plan → Work → Review → Compound
```

Use the plugin commands:
- `/workflows:brainstorm` — Explore requirements and approaches before planning
- `/workflows:plan` — Create implementation plans with research agents
- `/workflows:work` — Execute work items systematically with progress tracking
- `/workflows:review` — Run comprehensive code reviews (12+ parallel agents)
- `/workflows:compound` — Document solved problems to compound team knowledge

**IMPORTANT:** After every cycle, run `/workflows:compound` to update the Learnings section below.

---

## Bash Commands

```bash
# Development
pnpm dev                 # Start dev server
pnpm build               # Production build

# Verification (YOU MUST run before completing any task)
pnpm typecheck           # TypeScript check
pnpm lint                # ESLint
pnpm test                # Run tests

# Database
pnpm db:start            # Start local Supabase
pnpm db:types            # Regenerate types from schema
```

---

## Code Style

- TypeScript strict mode — never use `any`
- Use `interface` for objects, `type` for unions
- Named exports, not default exports
- Early returns over nested conditionals
- Keep files under 200 lines
- Prefer duplication over premature abstraction

---

## Engineering Decisions

**CRITICAL: Write to `DECISIONS.md` IMMEDIATELY — not later, not at the end of the session, RIGHT NOW when the decision happens.**

### What counts as a decision

Any time the user selects between options, agrees to an approach, or a choice is made about:
- APIs, services, or external integrations
- Libraries, packages, or dependencies
- Architecture patterns or data flow
- Authentication, storage, or infrastructure choices
- Workflows, processes, or tooling
- User experience patterns (progress indicators, notifications, etc.)
- Feature scope or MVP boundaries

### Automatic recording rules

1. **When you present options and the user picks one** — Immediately after the user responds, write the decision to `DECISIONS.md` before doing anything else. Do not continue implementation until the decision is recorded.
2. **When you recommend an approach and the user agrees** — That agreement is a decision. Write it to `DECISIONS.md` immediately.
3. **When the user states a preference unprompted** (e.g., "let's use Redis for caching") — Write it to `DECISIONS.md` immediately.
4. **When implementation forces a choice** (e.g., you pick library A over library B for a technical reason) — Write it to `DECISIONS.md` immediately and tell the user what you recorded.

### How to record

1. **Read `DECISIONS.md` first** — Check for conflicts with existing decisions.
2. **Use the next available `DECISION-XXX` number.**
3. **Write the entry using the Edit tool** — Add it to the correct category section in `DECISIONS.md` with all required fields (Date, Status, Context, Decision, Alternatives Considered, Consequences).
4. **If it supersedes an old decision** — Update the old entry's status to `Superseded by DECISION-XXX` and add an entry to the "Decision Changes" section.

### Non-negotiable

- Do NOT batch decisions for later. Each decision gets written the moment it's made.
- Do NOT skip recording because the decision feels small. If it affects how the project is built, it goes in the log.
- Do NOT ask "should I record this?" — just record it. The user can always remove entries they don't want.
- If you realize you forgot to record a decision from earlier in the conversation, stop what you're doing and record it now.

---

## Deployment

**Auto-deploy to Vercel:** Pushing to `main` automatically triggers a Vercel deployment.

- Production deploys from `main` branch
- Preview deploys from pull requests
- No manual deploy commands needed — just push to Git

If Vercel is not yet connected, set it up at [vercel.com](https://vercel.com) by importing the Git repository.

---

## GitHub Account & Repository Management

**IMPORTANT: At the start of every new project, before creating any repository or making any commits, ask me:**

> "Is this a personal project or a Kambo project?"

Then configure everything according to the answer:

### If Personal Project
- **GitHub owner:** `drewe4point0`
- **Repo URL pattern:** `github.com/drewe4point0/<repo-name>`
- **Git identity:** Use global git config (personal defaults)
- **Visibility:** Confirm with me whether public or private

### If Kambo Project
- **GitHub owner:** `KamboEnergyGroup`
- **Repo URL pattern:** `github.com/KamboEnergyGroup/<repo-name>`
- **Git identity:** Set repo-level config:
```bash
  git config user.name "Drewe - Kambo Energy"
  git config user.email "Apps@Kambo.com"
```
- **Visibility:** Default to **private** unless I say otherwise

### Guardrails
- **Never** create a repo under `drewe4point0` for Kambo work, or under `KamboEnergyGroup` for personal work. If unsure, stop and ask.
- **Before the first push** of any new project, confirm the remote URL with me so I can verify it's pointing to the correct account/org.
- When running `gh repo create`, always explicitly pass `--org KamboEnergyGroup` for Kambo projects or `--owner drewe4point0` for personal projects so ownership is never ambiguous.
- After setting repo-level git config for Kambo projects, run `git config user.email` and show me the output to confirm it's set correctly before committing.

---

## Workflow

1. **Plan first** — Use Plan Mode (shift+tab twice). Go back and forth until the plan is solid. Then switch to auto-accept and execute.

2. **Verify your work** — This is the most important thing. Give Claude a way to verify: run tests, check the browser, use a simulator. Verification improves quality 2-3x.

3. **Commit atomically** — One logical change per commit. Use conventional commits:
   - `feat:` new feature
   - `fix:` bug fix
   - `refactor:` code change that doesn't fix/add
   - `docs:` documentation only

4. **Update CLAUDE.md** — When Claude does something wrong, add it below so it doesn't happen again.

5. **Deploy** — Push to `main` to deploy. Vercel handles the rest automatically.

---

## Stack

| Layer | Tech |
|-------|------|
| Framework | Next.js 14 (App Router) |
| Database | Supabase |
| Styling | Tailwind CSS |
| Validation | Zod |
| Package Manager | pnpm |

---

## Patterns

### API Response
```typescript
type Result<T> = { ok: true; data: T } | { ok: false; error: string };
```

### Zod Validation
```typescript
const schema = z.object({ email: z.string().email() });
const result = schema.safeParse(input);
if (!result.success) return { ok: false, error: result.error.issues[0].message };
```

### Error Handling
```typescript
function getErrorMessage(error: unknown): string {
  if (error instanceof Error) return error.message;
  return String(error);
}
```

---

## Structure

```
/src
  /app          # Pages and API routes
  /components   # UI components
  /lib          # Business logic, Supabase client
  /types        # TypeScript types

DECISIONS.md    # Engineering decisions log (check before making new decisions)
```

---

## Learnings

**IMPORTANT:** Update this section after every `/workflows:compound`. This is where knowledge compounds.

### What Works
<!-- Document patterns that work well. Format: pattern → why it works -->


### What to Avoid
<!-- Document mistakes so they don't repeat. Format: mistake → correct approach -->


### Reusable Components
<!-- Document components built for reuse. Format: Name → path — description -->


---

## Project Notes

<!-- Add project-specific warnings, gotchas, and critical context here -->