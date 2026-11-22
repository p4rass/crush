# PLAN — task checklist
Tick items as they finish. One milestone per session is a good pace.

## M0 Setup
- [x] Project structure
- [ ] Finalise SPEC open questions
- [ ] `.env` with keys; first Crustdata call works

## M1 Data layer (code, no LLM)
- [ ] `src/crust.py`: client wrapper — headers, retry/backoff on 429, cache to `data/cache/`
- [ ] Each fact stored with source + fetched_at (`src/store.py`, SQLite)
- [ ] Company Identify -> one ID per company
- [ ] Tests for wrapper (mocked responses)

## M2 One request end to end (rough)
- [ ] Client company -> 3 competitors -> basic dossier -> Markdown report

## M3 Competitor discovery (multi-method, evidence per competitor)

## M4 Full dossier dimensions + analysis (inferred moves with citations)

## M5 Verification pass (every claim cites a stored fact) + robustness
- [ ] Resume after crash · dedupe jobs · conflicting sources · stealth company

## M6 Demo
- [ ] Backtest case · README · 2-min video · diagram
