# Crustdata API — quick reference
Docs: https://docs.crustdata.com (API reference, pricing, rate limits, llms.txt)
Base: https://api.crustdata.com
Headers: `authorization: Bearer KEY` · `x-api-version: 2025-11-01` · `content-type: application/json`
Overall cap: 200 req/min per key.

| API | Gives | Req/min |
|---|---|---|
| Person Search | people by title, employer (current/past), skills, education, location | 30 |
| Person Enrich | full career history with dates, education, skills | 15 |
| Company Search | companies by industry, size, growth, funding, location | 30 |
| Company Identify (FREE) | name/domain -> one company + confidence | 30 |
| Company Enrich | headcount over time, funding, leadership, web traffic | 15 |
| Job Search | postings by company, role, location | 30 |
| Web Search and Fetch | web/news/academic search; fetch a page | 10 |
| Watcher | webhook when a person/company/job changes | 10 |
| MCP server | https://install.crustdata.com/mcp | — |

Cost example: company search 0.03 credits per result (+ premium field groups).
Balance: `GET /account/credits` (free).

## Examples
```bash
curl -X POST https://api.crustdata.com/company/identify \
  -H "authorization: Bearer $CRUSTDATA_API_KEY" -H "content-type: application/json" \
  -H "x-api-version: 2025-11-01" -d '{"domains":["crustdata.com"]}'

curl -X POST https://api.crustdata.com/person/search ... \
  -d '{"filters":{"field":"education.schools.school","type":"=",
       "value":"Indian Institute of Technology, Kanpur"},"limit":1}'
```

## Errors
401 key not sent right · 402 out of credits (don't retry) · 403 no access to endpoint ·
429 rate limited (wait `x-ratelimit-reset`, retry) · no results: loosen one filter,
get exact values from Autocomplete API.

## To verify (unknowns)
- [ ] Exact endpoint paths/fields for enrich, job search, web search
- [ ] How far back headcount history and job postings go
- [ ] Whether reviews (employee/product) are exposed
