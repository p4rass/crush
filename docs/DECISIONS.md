# DECISIONS & LEARNINGS
Append-only. Judges ask: approaches considered, why this one, what worked,
what didn't, hardest case, what was left out. This file is where that comes from.

Format:
## YYYY-MM-DD — short title
- Options considered:
- Chose / why:
- Worked / didn't:

---

## 2026-11-22 — Product idea
- Options considered: KYB vendor check, insurance verification, competitive intelligence.
- Chose: competitive intelligence — deliverable is standardised, data-heavy,
  matches theme "forecast a rival's next launch from who it is hiring", backtestable.

## 2026-11-22 — Crustdata access
- Options: Crustdata MCP server vs own wrappers over REST API.
- Chose: own wrappers (control over retries, caching, source logging).
  MCP used only for exploring data during development.

## 2026-11-22 — Orchestration
- Chose: plain Python fixed pipeline; LLM only inside judgement steps.
  LangGraph only if its checkpointing saves time.
