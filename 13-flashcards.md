# DP-800 Flashcards

> Click any card to reveal the answer.

<section class="fc-section" data-fc-title="Design and develop">
<h2>1 - Design and develop</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">Track every row version automatically?</div><div class="fc-a"><strong>Temporal table</strong> (system-versioned).</div></div>

<div class="flashcard"><div class="fc-q">Tamper-evident audit trail in SQL?</div><div class="fc-a"><strong>Ledger table</strong> (append-only or updateable).</div></div>

<div class="flashcard"><div class="fc-q">Query parquet in ADLS without import?</div><div class="fc-a"><strong>External table</strong> (PolyBase).</div></div>

<div class="flashcard"><div class="fc-q">Many-to-many traversal pattern?</div><div class="fc-a">Graph node + edge tables; query with <code>MATCH</code>.</div></div>

<div class="flashcard"><div class="fc-q">Parse JSON into rows?</div><div class="fc-a"><code>OPENJSON</code> with optional <code>WITH</code> schema.</div></div>

<div class="flashcard"><div class="fc-q">Recursive hierarchy query?</div><div class="fc-a">Recursive <strong>CTE</strong> (<code>OPTION (MAXRECURSION 0)</code> for unlimited).</div></div>

<div class="flashcard"><div class="fc-q">Window function previous row?</div><div class="fc-a"><code>LAG()</code> over partition / order.</div></div>

<div class="flashcard"><div class="fc-q">Approximate string match function?</div><div class="fc-a"><code>EDIT_DISTANCE</code> or <code>SOUNDEX</code> / <code>DIFFERENCE</code>.</div></div>

</div>
</section>

<section class="fc-section" data-fc-title="Security">
<h2>2 - Security</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">Engine cannot see plaintext column?</div><div class="fc-a"><strong>Always Encrypted</strong> (AE) - keys at client.</div></div>

<div class="flashcard"><div class="fc-q">AE with rich predicates (range / LIKE)?</div><div class="fc-a">AE <strong>with secure enclaves</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Hide last 4 digits of SSN to non-admins?</div><div class="fc-a"><strong>Dynamic Data Masking</strong>. Note: presentation only - not a security boundary.</div></div>

<div class="flashcard"><div class="fc-q">Filter rows per tenant transparently?</div><div class="fc-a"><strong>Row-Level Security</strong> with predicate function.</div></div>

<div class="flashcard"><div class="fc-q">App connects without password?</div><div class="fc-a"><strong>Managed Identity</strong> + Entra ID auth.</div></div>

<div class="flashcard"><div class="fc-q">Track DML and logins?</div><div class="fc-a"><strong>Auditing</strong> -> Log Analytics / Storage / Event Hubs.</div></div>

</div>
</section>

<section class="fc-section" data-fc-title="Performance and deploy">
<h2>3 - Performance and deploy</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">Built-in query perf flight recorder?</div><div class="fc-a"><strong>Query Store</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Parameter-sensitive perf optimization?</div><div class="fc-a">PSP optimization (part of IQP).</div></div>

<div class="flashcard"><div class="fc-q">Schema-as-source artifact?</div><div class="fc-a"><strong>SQL Database Project</strong> (.sqlproj) -> DACPAC.</div></div>

<div class="flashcard"><div class="fc-q">Auto REST + GraphQL on schema?</div><div class="fc-a"><strong>Data API Builder</strong> (DAB).</div></div>

<div class="flashcard"><div class="fc-q">Stream row changes to Event Hubs?</div><div class="fc-a"><strong>Change Event Streaming (CES)</strong>.</div></div>

<div class="flashcard"><div class="fc-q">React in code to row insert?</div><div class="fc-a">Azure Functions <strong>SQL trigger</strong> (uses Change Tracking).</div></div>

<div class="flashcard"><div class="fc-q">Deploy from GitHub Actions without secrets?</div><div class="fc-a">OIDC + <strong>federated credential</strong> with Entra ID.</div></div>

</div>
</section>

<section class="fc-section" data-fc-title="AI capabilities">
<h2>4 - AI capabilities</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">Call Azure OpenAI from T-SQL?</div><div class="fc-a"><code>sp_invoke_external_rest_endpoint</code> with Database Scoped Credential.</div></div>

<div class="flashcard"><div class="fc-q">Fixed-dim float column type?</div><div class="fc-a"><strong>VECTOR(N)</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Top-K nearest neighbor T-SQL?</div><div class="fc-a"><code>VECTOR_SEARCH</code> or <code>ORDER BY VECTOR_DISTANCE</code>.</div></div>

<div class="flashcard"><div class="fc-q">Fast vector index, recall under 100%?</div><div class="fc-a"><strong>ANN</strong> (approximate).</div></div>

<div class="flashcard"><div class="fc-q">Best metric for normalized text embeddings?</div><div class="fc-a"><strong>Cosine</strong> distance.</div></div>

<div class="flashcard"><div class="fc-q">Merge keyword + vector ranks fairly?</div><div class="fc-a">Hybrid search + <strong>RRF (Reciprocal Rank Fusion)</strong>.</div></div>

<div class="flashcard"><div class="fc-q">Ground LLM in DB content?</div><div class="fc-a"><strong>RAG</strong>: vector search top-K -> LLM with citations.</div></div>

</div>
</section>

<section class="fc-section" data-fc-title="Gotchas">
<h2>5 - Gotchas</h2>

<div class="flashcard-grid">

<div class="flashcard"><div class="fc-q">Embedding dimension mismatch impact?</div><div class="fc-a">All distances meaningless; rebuild index after re-embed.</div></div>

<div class="flashcard"><div class="fc-q">Recursive CTE default cap?</div><div class="fc-a">100 levels. Use <code>OPTION (MAXRECURSION 0)</code> for unlimited.</div></div>

<div class="flashcard"><div class="fc-q">DDM weakness?</div><div class="fc-a">Privileged users / `UNMASK` permission see plaintext.</div></div>

<div class="flashcard"><div class="fc-q">DACPAC blocks drop column?</div><div class="fc-a">Default <code>BlockOnPossibleDataLoss=true</code>.</div></div>

<div class="flashcard"><div class="fc-q">SQL trigger requirement?</div><div class="fc-a">Change Tracking must be enabled on the table.</div></div>

<div class="flashcard"><div class="fc-q">JSON_VALUE on missing path?</div><div class="fc-a">Returns NULL in lax mode (default); use strict to error.</div></div>

</div>
</section>

---

[Master Index](00-MASTER-INDEX.md)
