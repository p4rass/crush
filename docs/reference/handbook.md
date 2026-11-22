# ContextCon 04 handbook — what matters for the build

## Rules
- New public repo; commit history starts at build start. Commit as you go.
- Any model/framework/tool allowed. Crustdata optional (judged the same either way).
- Agents talk only to own team / organisers during event (no real outside people).
- Keep notes as you build (-> docs/DECISIONS.md).

## Submission
Public repo + README · one 2-min demo video link (plays in private window) ·
public diagram link · "how it works": service replaced, approach, models used, what next.

## Judging (100)
| Criterion | Pts | Means |
|---|---|---|
| End-to-end execution | 25 | real request in, finished result out, no human in the middle |
| Facts and verification | 20 | every fact right for its date, reasons + sources, one entity = one record, says when it can't check |
| Robustness / edge cases | 20 | messy input, missing fields, tool timeouts/nonsense, resumes after crash, never sends/pays twice |
| Customer value / idea | 20 | job businesses pay for; non-obvious approach; more than chat-on-a-model |
| Demo and understanding | 15 | clear demo; approaches weighed, what worked/didn't, hardest case, next |
Ties: end-to-end, then facts.

## Judges want to hear
Service + who pays · approaches considered and why this one · what worked/didn't ·
hardest case · how tested · what was left out · what next and why not now.

## Demo tips
Open with the request in customer words; run start to finish; show where each fact
came from; show a duplicate / changed fact / failing call if possible; backup video.

## Theme lines this project hits
- Revenue: "Forecast a rival's next launch from who it is hiring."
- Research and markets: results scored on real numbers published after the model was trained.
