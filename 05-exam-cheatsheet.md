# DP-800 Exam Decision Reference

> Fast lookup table by problem wording. Use during review.

## Tables

| Wording | Pick |
|---|---|
| "ultra-low-latency point inserts" | In-memory OLTP table |
| "track every row version automatically" | Temporal (system-versioned) table |
| "query parquet in ADLS without import" | External table |
| "tamper-evident audit trail" | Ledger table |
| "many-to-many traversal" | Graph node + edge with `MATCH` |
| "semi-structured payload" | JSON column / NVARCHAR + JSON funcs |

## T-SQL

| Wording | Pick |
|---|---|
| "rolling sum / lag prev row" | Window function (`SUM() OVER`, `LAG()`) |
| "self-referential hierarchy" | Recursive CTE |
| "regex pattern match" | `REGEXP_LIKE` / `REGEXP_REPLACE` |
| "approximate string match" | `EDIT_DISTANCE` / `SOUNDEX` |
| "transaction error rollback" | `BEGIN TRY ... CATCH` + `THROW` |

## Security

| Wording | Pick |
|---|---|
| "engine cannot read column" | Always Encrypted (with enclave for predicates) |
| "hide last 4 of SSN to non-admin" | Dynamic Data Masking |
| "filter rows per tenant" | Row-Level Security |
| "no DB password from web app" | Managed Identity + Entra ID auth |
| "track DML and login events" | Auditing |

## Performance

| Wording | Pick |
|---|---|
| "find top regressed queries" | Query Store -> Top Resource Consumers |
| "missing index hint" | `sys.dm_db_missing_index_details` |
| "wait stat analysis" | `sys.dm_os_wait_stats` |
| "adaptive query plan" | Intelligent Query Processing |
| "param-sensitive perf" | PSP optimization (IQP) |

## Deploy

| Wording | Pick |
|---|---|
| "VS Code project for SQL" | SQL Database Projects (.sqlproj) |
| "compile schema artifact" | DACPAC |
| "auto REST + GraphQL on schema" | Data API Builder |
| "deploy from GitHub Actions, no PAT" | OIDC + federated credential |

## Integrate

| Wording | Pick |
|---|---|
| "row changes to Event Hubs in real time" | Change Event Streaming (CES) |
| "polling-based ETL of changes" | Change Data Capture (CDC) |
| "Function fires on table change" | Azure Functions SQL trigger |
| "DB-level resource events" | Event Grid integration |

## AI

| Wording | Pick |
|---|---|
| "call Azure OpenAI from T-SQL" | `sp_invoke_external_rest_endpoint` |
| "fixed-dim float vector column" | `VECTOR(N)` |
| "fast top-K vector search" | Vector index ANN + `VECTOR_SEARCH` |
| "exact nearest neighbor" | ENN |
| "best of keyword + vector" | Hybrid search + RRF |
| "ground LLM in DB content" | RAG inside SQL |

## Common gotchas

- Embedding dimension mismatch -> meaningless distances.
- DDM is presentation only; not a security boundary.
- Always Encrypted without enclave blocks complex predicates.
- DACPAC `BlockOnPossibleDataLoss=true` stops every drop column.
- Functions SQL trigger requires Change Tracking enabled.
- Memory-optimized tables have row-size + durability constraints.
- Recursive CTE caps at 100 levels by default; use `OPTION (MAXRECURSION 0)` for unlimited.

---

[Master Index](00-MASTER-INDEX.md)
