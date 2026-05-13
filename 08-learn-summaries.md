# DP-800 Microsoft Learn Path Summaries

> Condensed take-aways from official DP-800 learning paths.

## Path 1: Develop database solutions in Azure SQL

- Use modern table types deliberately (in-memory, temporal, ledger, graph).
- JSON columns or `NVARCHAR(MAX)` + JSON functions for flexible payloads.
- Master CTEs and window functions; they replace many subqueries.
- Use GitHub Copilot in your editor for boilerplate; review every suggestion.

## Path 2: Secure and optimize Azure SQL

- Always Encrypted protects data from the engine; DDM and RLS protect from queries.
- Managed Identity removes secrets from connection strings.
- Query Store is the perf flight recorder - enable everywhere.
- Intelligent Query Processing improves perf without code changes.

## Path 3: Deploy and integrate Azure SQL

- SQL Database Projects + DACPAC + GitHub Actions = modern deployment.
- Data API Builder spins up REST + GraphQL on a schema config.
- CDC for batch ETL, CES for streaming, SQL trigger for code-driven reactions.

## Path 4: Implement AI capabilities in Azure SQL

- Embeddings live as `VECTOR(N)` columns.
- Use ANN indexes for speed, ENN for exact.
- Hybrid (vector + full-text) + RRF beats either alone for general queries.
- RAG inside SQL pairs vector search with `sp_invoke_external_rest_endpoint`.

---

[Master Index](00-MASTER-INDEX.md)
