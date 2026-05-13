# DP-800 Extra Concepts

> Subtle distinctions that show up in exam wording.

## Always Encrypted variants

| Variant | Predicate support | Key in |
|---|---|---|
| Deterministic AE | Equality only | Client app via Key Vault |
| Randomized AE | None (server side) | Client app via Key Vault |
| AE with secure enclaves | Range, LIKE, sorting | VBS or Intel SGX enclave on server |

## Updateable vs Append-Only ledger

| Trait | Updateable | Append-only |
|---|---|---|
| INSERT | Yes | Yes |
| UPDATE / DELETE | Yes (history kept) | No |
| Use case | Slowly changing dim with audit | Immutable audit log |

## Vector index types

| Type | Recall | Speed |
|---|---|---|
| ENN | 100% | Slow (full scan) |
| ANN | <100% (configurable) | Fast (sub-linear) |

## CDC vs Change Tracking vs CES

| Feature | CDC | Change Tracking | CES |
|---|---|---|---|
| Granularity | Column-level | Primary key only | Row-level JSON |
| Storage | Shadow tables | Internal | Streamed out |
| Latency | Polling | Polling | Push to Event Hubs |
| Best for | Classic ETL | Sync apps | Event-driven analytics |

## Distance metrics

| Metric | When |
|---|---|
| Cosine | Direction matters; magnitude irrelevant (most LLM embeddings) |
| Euclidean | Magnitude matters |
| Dot product | When magnitude encodes importance (after normalize) |

## sp_invoke_external_rest_endpoint security

- Use **Database Scoped Credential** with Managed Identity.
- Endpoint must be in the allowed firewall list (Outbound traffic via VNet rules).
- Throttled per database; expect 429 on bursts.

## RRF formula

For multiple ranked lists L1..Lm and a result d, score is:

```
RRF(d) = sum over i of (1 / (k + rank_i(d)))
```

- `k` typically 60.
- Result reranked by descending `RRF(d)`.

## SQL Database Projects vs DACPAC

- `.sqlproj` is the **source**.
- DACPAC is the **build artifact** (zip with model.xml + scripts).
- Deploy DACPAC with `sqlpackage /Action:Publish` or `Microsoft.Build.Sql` task.

## Microsoft Purview integration

- Auto-classify columns (PII, financial).
- Lineage from Azure SQL through Fabric / ADF.
- Apply sensitivity labels surfaced in apps respecting DDM/RLS.

---

[Master Index](00-MASTER-INDEX.md)
