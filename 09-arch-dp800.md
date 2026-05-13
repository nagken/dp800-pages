# DP-800 Reference Architectures

> Canonical AI-enabled database patterns. Memorize the shapes.

## 1. RAG inside Azure SQL

```mermaid
flowchart LR
    Docs[Source documents] --> Chunk[Chunker]
    Chunk --> Tbl[Docs table content + VECTOR col]
    Tbl --> Idx[ANN vector index]
    Q[User question] --> Embed1[Embed via Azure OpenAI]
    Embed1 --> VS[VECTOR_SEARCH top-K]
    VS --> RRF[RRF rerank w/ full-text]
    RRF --> Ctx[Context]
    Ctx --> LLM[Azure OpenAI completion]
    LLM --> Ans[Grounded answer + citations]
```

## 2. Streaming change architecture

```mermaid
flowchart LR
    OLTP[Azure SQL DB] -- CES --> EH[Event Hubs]
    EH --> Func[Azure Function SQL trigger / Stream]
    EH --> ASA[Stream Analytics]
    ASA --> ADX[Azure Data Explorer]
    ADX --> RTD[Real-Time Dashboards]
    Func --> Webhook[App webhook]
```

- CES pushes JSON row events; Stream Analytics aggregates; ADX retains hot.

## 3. CI/CD with SQL Database Projects

```mermaid
flowchart LR
    Dev[VS Code .sqlproj] --> PR[Pull Request]
    PR --> CI[GitHub Actions build]
    CI --> Dac[DACPAC artifact]
    Dac --> DepDev[Deploy to Dev DB]
    DepDev --> Test[Schema + integration tests]
    Test --> Approval[Environment approval]
    Approval --> Prod[Deploy to Prod DB]
    Prod -. OIDC federated cred .- AzAD[Microsoft Entra]
```

## 4. Always Encrypted with secure enclaves

```mermaid
flowchart LR
    Client[App client] -- ColumnEncKey via Key Vault --> Driver[SQL driver]
    Driver -- ciphertext + range query --> Engine[Azure SQL engine]
    Engine -- delegates predicate --> Enclave[VBS / SGX enclave]
    Enclave -- decrypts inside enclave --> Result
    Result --> Driver
    Driver --> Client
```

## 5. Data API Builder front-end

```mermaid
flowchart LR
    Schema[Tables / views] --> DAB[Data API Builder config]
    DAB --> Rest[/REST/]
    DAB --> Gql[/GraphQL/]
    Rest --> Web[Web client]
    Gql --> Mobile[Mobile client]
    DAB -. Entra JWT .- AzAD[Microsoft Entra ID]
    DAB --> SQL[Azure SQL DB]
```

---

[Master Index](00-MASTER-INDEX.md)
