# Crush — Competitive Intelligence Agent (ContextCon hackathon)

Given one company, find its competitors, collect everything knowable about them
(Crustdata + web), and deliver a sourced CI report plus change alerts.

## Start of every session
1. Read `STATUS.md` (current state, next task).
2. Read the newest file in `handoffs/` if STATUS.md points to it.
3. Read `docs/SPEC.md` / `docs/PLAN.md` only when the task needs them.

## End of every session (or when context is ~50% full)
Run `/handoff`. It updates `STATUS.md`, writes `handoffs/NNN-topic.md`,
and logs decisions in `docs/DECISIONS.md`. Skip the handoff file if the work
ended at a clean stopping point; still update STATUS.md.

## Rules
- IMPORTANT: facts come from API/web responses, never model memory. Every fact
  stored with source (endpoint or URL) + fetched-at date. Unknown -> "not verified".
- Mechanical work in code (API calls, retries, dedupe, maths, caching, state).
  LLM only for judgement (pick competitors, interpret signals, write report).
- Always resolve companies via Company Identify before storing (one ID per company).
- Cache every API response in `data/cache/` (saves credits). Never commit `data/` or `.env`.
- Retry 429/timeouts with backoff; read `x-ratelimit-reset`. 402 = out of credits, don't retry.
- Save pipeline progress after each step so a crash resumes, not restarts.
- Plan first for anything touching >1 file; small fixes: just do it.
- After a change, run it (or its test) and show the output before saying done.
- Keep files small and modules single-purpose.

## Layout
- `src/` code · `tests/` tests · `data/cache/` API cache (gitignored)
- `docs/SPEC.md` what we build · `docs/PLAN.md` task checklist
- `docs/DECISIONS.md` approaches tried, what worked/failed (feeds README + demo)
- `docs/reference/` handbook + Crustdata API notes (read on demand)
- `handoffs/` session handoffs · `STATUS.md` one-screen current state

## Env
- Python 3.11+, keys in `.env` (see `.env.example`).
- Crustdata: base `https://api.crustdata.com`, headers
  `authorization: Bearer $CRUSTDATA_API_KEY`, `x-api-version: 2025-11-01`.
