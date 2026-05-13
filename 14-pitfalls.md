# DP-800 Pitfalls

> Mistakes that cost points and pages.

## Tables

- In-memory OLTP without enough memory -> degraded perf or insert errors.
- Temporal history grows forever -> set retention policy.
- External tables not push-down -> full data shipped to engine.
- Ledger updateable vs append-only confusion -> wrong audit semantics.
- Graph queries without indexes on edge endpoints -> full scans.

## JSON and T-SQL

- `JSON_VALUE` lax (default) returns NULL on missing path; use strict mode to throw.
- Recursive CTE caps at 100 levels - hit silent in deep hierarchies.
- Window functions without `ROWS BETWEEN` -> running aggregates can be wrong.
- `REGEXP_*` functions only on modern Azure SQL; not in older SQL Server.

## AI-assisted dev

- Trusting Copilot output without compile + test -> plausible-but-wrong T-SQL.
- MCP server exposes too much schema -> data leakage to AI agents.
- Embedding generation in tight loop calls Azure OpenAI per row -> 429 storm and cost spike.

## Security

- AE without enclave -> complex predicates fail silently or run client-side only.
- DDM treated as security -> a `UNMASK` user sees plaintext.
- RLS using `USER_NAME()` not `SESSION_CONTEXT()` -> wrong filter under app pooling.
- Managed Identity granted role at server level when DB level was enough -> overscoped.

## Performance

- Query Store off -> blind to perf regressions.
- Statistics stale after big load -> bad plans. `UPDATE STATISTICS` post-load.
- IQP off -> miss adaptive joins / batch mode wins.
- Wrong index strategy: nonclustered when columnstore was right (analytics workload).

## Deploy

- DACPAC `BlockOnPossibleDataLoss=true` blocks drop column - tune per env.
- GitHub Actions still using PAT instead of OIDC + federated credential.
- Pre / post-deploy scripts not idempotent -> re-deploy fails.
- DAB exposed without auth -> public CRUD on DB.

## Integrate

- CES configured but downstream Event Hubs throttled -> back-pressure on SQL.
- CDC retention too low -> ETL misses changes.
- SQL trigger function without Change Tracking enabled -> never fires.

## AI

- Wrong distance metric (cosine vs euclidean) -> rankings flip.
- Vector index built before column populated -> rebuild required.
- Skipping chunk overlap -> answers truncated at chunk boundary.
- RAG without citations -> users cannot verify.
- Hybrid search ranks combined naively (sum of scores) instead of RRF -> bias.

---

[Master Index](00-MASTER-INDEX.md)
