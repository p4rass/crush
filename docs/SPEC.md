# SPEC — Competitive Intelligence Agent

## Service replaced
CI analysts / CI firms that produce competitor landscapes, dossiers and
monitoring reports for strategy, product and sales teams.

## Input
- Company name or domain (required)
- Optional focus: product line, region, competitors the client already knows

## Output (the report)
1. Executive summary — 3 things that changed and what to do
2. Landscape — direct / adjacent / emerging competitors, evidence for each
3. Dossier per competitor (dimensions below)
4. Inferred moves — with confidence + sources
5. Comparison table (client vs competitors)
6. Gaps — what couldn't be verified

## Pipeline
1. Identify client (Company Identify) -> Enrich
2. Discover competitors (keep if found by 2+ methods):
   similar companies (Company Search) · "X alternatives"/"X vs" (Web Search) ·
   talent flow (Person Search on past employer) · hiring overlap (Job Search) ·
   shared investors/customers (Enrich, Web Fetch)
3. Collect per competitor
4. Analyse (LLM) -> claims, each linked to stored facts
5. Verify: every claim in report cites a stored fact; else drop or mark unverified
6. Render report (Markdown/HTML)
7. Monitor (stretch): Watcher webhooks + page diffs

## Data dimensions per competitor
| Dimension | Source |
|---|---|
| Basics (founded, HQ, size, description) | Identify, Enrich |
| Headcount over time / by function | Company Enrich |
| Hiring: roles, seniority, locations, tech in JDs | Job Search |
| Leadership + senior hires/exits | Enrich, Person Enrich |
| Talent flow in/out | Person Search/Enrich |
| Funding rounds, investors | Enrich, Web Search |
| Web traffic trend | Company Enrich |
| Product, pricing, changelog | Web Fetch |
| News, launches, partnerships, layoffs | Web Search |
| Customers, GTM, regions | Web Fetch, Job Search |

## Known limits (state in report)
No revenue / customer counts / private pricing. Headcount undercounts non-LinkedIn
staff. Job ads can be ghost/duplicate. Inferences are forecasts.

## Hard cases to handle + demo
- Two companies with same/similar name
- Stealth competitor with little data -> say so, don't guess
- Duplicate job postings
- Sources disagree
- API 429 / timeout / empty result
- Crash mid-run -> resumes

## Demo idea
Backtest: give the agent only data from before a real past launch; show it predicted it.

## Open questions
- [ ] Stack: plain Python + Anthropic SDK? (default) or Agent SDK / LangGraph
- [ ] Report format: Markdown -> HTML?
- [ ] Interface: CLI first; UI only if time remains
- [ ] Credit budget per report

## Out of scope (for now)
Multi-user, auth, deployment, scheduling.
