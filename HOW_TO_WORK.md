# How to work on Crush with Claude

Open Claude Code in `D:\crush` (`cd D:\crush` then `claude`).
`CLAUDE.md` loads by itself every session.

## Every session
1. **Start:** type `/resume`.
2. **One task per session.** Pick it from `STATUS.md` / `docs/PLAN.md`.
3. **Big task (more than 1 file)?** Press `Shift+Tab` for plan mode, approve the plan, then build.
4. **Make it prove it:** "run it and show me the output" before you accept "done".
5. **End, or context ~50% full:** type `/handoff`, then `/clear` (or open a new session) and `/resume`.

## Habits that help
- Wrong twice on the same thing? `/clear` and re-ask with what you learned.
- Big lookups ("read all the docs", "explore the API"): say "use a subagent".
  This keeps your main context clean.
- Quick side question: `/btw <question>`. It stays out of context.
- Before finishing a milestone: "use the reviewer agent on this".
- Tried an approach? Make sure it lands in `docs/DECISIONS.md`. The README and demo are built from it.
- Commit after each working step.

## Files
| File | What |
|---|---|
| `STATUS.md` | where we are + next task (read first) |
| `handoffs/` | one file per unfinished session |
| `docs/SPEC.md` | what we're building |
| `docs/PLAN.md` | checklist |
| `docs/DECISIONS.md` | approaches, what worked/failed |
| `docs/reference/` | handbook + Crustdata API notes |
