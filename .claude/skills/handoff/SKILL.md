---
name: handoff
description: End-of-session handoff. Use when the user says handoff, wrap up, end session, or context is getting full.
disable-model-invocation: true
---
Write the session handoff so a fresh session can continue with zero re-explaining.

1. Overwrite `STATUS.md` (one screen): where we are, the single next task,
   blockers, path of the latest handoff.
2. If work is mid-way, create `handoffs/NNN-<topic>.md` from
   `handoffs/_TEMPLATE.md` (NNN = next number). Be concrete: file paths,
   commands to run, exact errors. Skip this step if the session ended at a
   clean stopping point.
3. Append any approach tried / decision / failure to `docs/DECISIONS.md`.
4. Tick finished items in `docs/PLAN.md`.
5. If code is in a good state, commit with a clear message.
6. Reply with: the path of the handoff and the one-line prompt to start the
   next session.
