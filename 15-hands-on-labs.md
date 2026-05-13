# DP-800 Hands-On Labs

> Practical exercises in Azure SQL DB (free tier or pay-go).

## Lab 1: Temporal + ledger

1. Create a table `Customers` with system-versioning enabled (temporal).
2. INSERT, UPDATE, DELETE; query `FOR SYSTEM_TIME AS OF` to see prior state.
3. Convert (or recreate) the table as **updateable ledger**.
4. Verify the ledger digest with `sys.sp_verify_database_ledger`.

## Lab 2: Vector search end-to-end

1. Provision Azure OpenAI; deploy `text-embedding-3-small`.
2. In Azure SQL: create `DATABASE SCOPED CREDENTIAL` with managed identity to OpenAI endpoint.
3. Create `Docs(id INT, content NVARCHAR(MAX), embedding VECTOR(1536))`.
4. Insert sample docs; populate `embedding` via `sp_invoke_external_rest_endpoint`.
5. Build an ANN vector index.
6. Query: embed user question, run `VECTOR_SEARCH` for top-5.

## Lab 3: Hybrid search + RRF

1. Add full-text index on `Docs.content`.
2. Run vector search top-20 + full-text search top-20.
3. Apply RRF (k=60) to merge.
4. Compare result set quality vs vector-only or full-text-only.

## Lab 4: SQL Database Project + GitHub Actions

1. In VS Code, create a new SQL Database Project from existing schema.
2. Commit to GitHub.
3. Add a workflow that builds DACPAC and deploys to dev DB using OIDC + federated credential.
4. Add an environment + approval for prod stage.

## Lab 5: Data API Builder

1. Create `dab-config.json` referencing the Azure SQL DB.
2. Run `dab start` locally; test REST + GraphQL endpoints.
3. Add Entra JWT auth.
4. Containerize and deploy to Azure Container Apps.

## Lab 6: Change Event Streaming

1. Create an Event Hubs namespace + hub.
2. On Azure SQL DB, enable Change Event Streaming for `Orders`.
3. Insert / update rows; observe events landing in Event Hubs.
4. Add a Stream Analytics job summarizing by minute.

## Lab 7: Always Encrypted with secure enclaves

1. Provision a DB with Always Encrypted with secure enclaves enabled.
2. Encrypt `Customers.SSN` (deterministic for equality search) and `Salary` (range with enclave).
3. Run a range query on Salary from a client with the column master key in Key Vault.
4. Verify ciphertext stays opaque server-side.

---

[Master Index](00-MASTER-INDEX.md)
