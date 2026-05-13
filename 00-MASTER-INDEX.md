# DP-800 - Developing AI-Enabled Database Solutions - Visual Study Guide

> Concept-only study aid. No exam questions reproduced. Source PDF (if any) stays local + gitignored.

**Skills outline:** https://learn.microsoft.com/credentials/certifications/resources/study-guides/dp-800

> [!NOTE]
> DP-800 is the **beta exam** for the new Microsoft Certified: SQL AI Developer Associate. Beta exams may evolve - always check the latest skills outline.

## Master mind map

```mermaid
mindmap
  root((DP-800))
    Design and develop
      Tables
        Standard
        In-memory OLTP
        Temporal
        External
        Ledger
        Graph
      JSON
        JSON columns
        OPENJSON
        FOR JSON
      T-SQL
        CTEs
        Window functions
        REGEXP_LIKE
        FUZZY match
        MATCH graph
        Error handling
      AI-assisted dev
        GitHub Copilot
        Copilot in Fabric
        MCP servers
    Secure optimize deploy
      Security
        Always Encrypted
        Dynamic Data Masking
        Row-Level Security
        Managed Identity
        Auditing
        Microsoft Purview
      Performance
        Query Store
        DMVs
        Intelligent Query Processing
        Indexes
      Deploy
        SQL Database Projects
        DACPAC
        CI/CD GitHub Actions
        Data API Builder
      Integrate
        CDC and CES
        Azure Functions SQL trigger
        Event Grid
    AI capabilities
      Embeddings
        sp_invoke_external_rest_endpoint
        Azure OpenAI
      Vector data type
        VECTOR
        Vector index ANN ENN
      Vector search
        VECTOR_DISTANCE
        VECTOR_SEARCH
      Full-text and semantic
        Full-text index
        Semantic search
        Hybrid search
        RRF
      RAG
        Grounding
        Chunking strategies
```

## Domain map

```mermaid
flowchart LR
    Master["DP-800 Master Index"]
    D01["Design and develop database solutions"]
    Master --> D01
    D02["Secure optimize and deploy"]
    Master --> D02
    D03["Implement AI capabilities"]
    Master --> D03
```

## Domain weights

```mermaid
pie showData
    title DP-800 domain weights
    "Design and develop" : 38
    "Secure optimize deploy" : 35
    "Implement AI capabilities" : 27
```

## Recommended study order

```mermaid
gantt
    title Suggested study plan
    dateFormat X
    axisFormat Day %d
    section Plan
    Design and develop      :t1, 0, 4d
    Secure optimize deploy  :t2, after t1, 3d
    Implement AI            :t3, after t2, 3d
    Cheatsheet and review   :t4, after t3, 1d
```

---

**Next:** open [01-design-and-develop.md](01-design-and-develop.md)
