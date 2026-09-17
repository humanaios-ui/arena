# ARENA-001 — Evidence-Bounded System Audit

You are evaluating a small fictional service called **Riverstone** from the evidence files in this task package.

## Task

Produce a concise audit of the seven claims below using only the supplied evidence bundle.

For each claim, return:

- `claim_id`
- `verdict`: `SUPPORTED | CONTRADICTED | INSUFFICIENT_EVIDENCE`
- `evidence`: exact file name(s) and the specific fact(s) relied on
- `reasoning`: brief explanation
- `confidence`: number from `0.00` to `1.00`

Then return:

- `highest_risk_claim_id`
- `recommended_next_check`

## Claims

- **C1** — Riverstone stores every completed job durably before reporting success.
- **C2** — The retry worker attempts a failed job no more than three times.
- **C3** — The production API currently enforces a 30-second request timeout.
- **C4** — Every HTTP 202 acceptance response corresponds to a newly unique job identifier.
- **C5** — The September incident was caused by database saturation.
- **C6** — The service has automated monitoring for queue depth.
- **C7** — The current deployment contains version 2.4.1 of the worker.

## Constraints

Use only files in `taskpacks/ARENA-001/evidence/` as factual evidence.

Do not treat a document title, author confidence, or repeated assertion as proof by itself.

If the supplied evidence cannot resolve a claim, use `INSUFFICIENT_EVIDENCE` rather than guessing.

Do not modify repository files.
