# DP-800 Glossary

| Term | Definition |
|---|---|
| **Azure SQL DB** | Managed relational service. |
| **Managed Instance** | Near-100% SQL Server compatibility on Azure. |
| **In-memory OLTP** | Memory-optimized tables + native compiled stored procs. |
| **Temporal table** | System-versioned table with hidden history. |
| **External table** | Read parquet/CSV in ADLS / S3 in place. |
| **Ledger table** | Tamper-evident table with cryptographic Merkle tree. |
| **Graph table** | NODE / EDGE table queried with `MATCH`. |
| **JSON data type** | Native JSON column with validation. |
| **OPENJSON** | T-SQL function to parse JSON into rows. |
| **CTE** | Common Table Expression. |
| **Window function** | Aggregation `OVER` partitions / order. |
| **REGEXP_LIKE** | Regex match T-SQL function (modern Azure SQL). |
| **MATCH** | Graph traversal predicate in SELECT. |
| **GitHub Copilot** | AI pair-programmer in VS Code / SSMS. |
| **MCP server** | Model Context Protocol service exposing schema/tools. |
| **Always Encrypted (AE)** | Client-side column encryption; engine only sees ciphertext. |
| **Secure enclaves** | VBS / SGX isolated computation enabling rich predicates over AE. |
| **Dynamic Data Masking (DDM)** | Presentation-layer mask. |
| **Row-Level Security (RLS)** | Predicate function filtering rows per user. |
| **Managed Identity (MI)** | Entra ID identity for Azure resource auth without secrets. |
| **Auditing** | DML / login event logging to Storage / LA / Event Hubs. |
| **Microsoft Purview** | Data classification + lineage governance. |
| **Query Store** | Built-in flight recorder for query perf. |
| **DMV** | Dynamic Management View / Function for diagnostics. |
| **IQP** | Intelligent Query Processing - adaptive plans. |
| **PSP** | Parameter Sensitivity Plan optimization (IQP). |
| **DACPAC** | Data-tier App Package - schema deployment artifact. |
| **SQL Database Project** | VS Code .sqlproj source for schema. |
| **Data API Builder (DAB)** | Auto REST + GraphQL gateway on schema. |
| **CDC** | Change Data Capture - polling-based change log. |
| **CES** | Change Event Streaming - push to Event Hubs. |
| **SQL trigger (Functions)** | Azure Function fires on table change (uses Change Tracking). |
| **Embedding** | Vector representation of text from LLM. |
| **VECTOR(N)** | Fixed-dim vector data type. |
| **ANN** | Approximate Nearest Neighbor index. |
| **ENN** | Exact Nearest Neighbor scan. |
| **VECTOR_DISTANCE** | Distance function (cosine / euclidean / dot). |
| **VECTOR_SEARCH** | Top-K nearest neighbor T-SQL function. |
| **Full-text search** | Keyword index with `CONTAINS` / `FREETEXT`. |
| **Semantic search** | Concept-keyword search (`SEMANTICKEYPHRASETABLE`). |
| **Hybrid search** | Vector + full-text combined. |
| **RRF** | Reciprocal Rank Fusion - merge ranked lists. |
| **RAG** | Retrieval-Augmented Generation. |
| **`sp_invoke_external_rest_endpoint`** | T-SQL stored proc to call REST APIs. |
| **Database Scoped Credential** | Auth bundle for external endpoints / data sources. |

---

[Master Index](00-MASTER-INDEX.md)
