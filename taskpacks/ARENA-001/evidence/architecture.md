# Riverstone architecture note

Revision: 2026-08-28

1. The public API accepts a job request and writes an envelope to the queue.
2. The API returns HTTP 202 after the queue acknowledges the envelope.
3. The worker later writes the completed result to PostgreSQL.
4. A successful HTTP 202 therefore means the job was accepted for processing; it does not mean the completed result has already been durably stored.
5. New job envelopes receive a UUIDv7 `job_id`.
6. Requests carrying the same valid `Idempotency-Key` may receive the existing `job_id` instead of creating a second job.
7. Once issued, `job_id` is not mutated.
