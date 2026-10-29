# Architecture Decision Record — EduAdvisor

| Decision | Requirement / Constraint | Alternatives Considered | Selected Option | Trade-off Accepted |
|---|---|---|---|---|
| Include knowledge access | Answers must be grounded in approved information | Base model only; static search; dynamic knowledge access | Generic knowledge-access component | More system complexity, but better grounding and traceability |
| Include scope control | Out-of-scope queries must be refused | Instruction only; explicit scope-control component | Explicit scope control | Possible false refusals and additional processing |




# Initial Requirements Traceability Matrix — EduAdvisor

| Objective | Requirement | Evaluation Criterion | Architecture Element | Later Evidence |
|---|---|---|---|---|
| **O1, O2** | **FR1:** Answer questions about course codes, titles, credits, and descriptions using the current catalogue. | **Answer Correctness:** ≥80% correct responses on supported academic queries, contributing to NFR2. | Document loading, cleaning, chunking, embeddings, ChromaDB retrieval, and model generation. | **Pending:** Course-information test results compared against the current official catalogue. |
| **O1, O2** | **FR2:** Answer prerequisite questions without deciding prerequisite waivers. | **Answer Correctness:** ≥80% correct responses, contributing to NFR2. **Additional check proposed:** Verify that waiver requests receive an appropriate redirect. | Catalogue retrieval, model instructions, and scope control. | **Pending:** Prerequisite test results and responses to waiver requests. |
| **O1, O2** | **FR3, RAI4:** Provide verifiable source references and indicate when supporting evidence is insufficient. | **Source Citation and Support:** 100% citation presence; ≥95% citation-source match. **Additional check needed:** Handling of insufficient evidence. | Knowledge access, retrieved document context, model instructions, and output citation check. | **Pending:** Citation audit and tests where source documents do not contain the answer. |
| **O2, O3** | **FR4, RAI2:** Refuse out-of-scope queries and redirect appropriately. | **Out-of-Scope Refusal:** ≥95% refusal-and-redirect success on at least 20 out-of-scope queries. | Explicit scope control and guardrails. | **Pending:** Safety/scope test results, including distress-related queries disguised as academic questions. |
| **O1, O2** | **FR5:** Present answers in clear language suitable for undergraduate students. | **Response Clarity:** Meet the defined clarity rubric. **Rubric and pass level remain to be specified.** | Model instructions and chat interface. | **Pending:** Completed clarity rubric scores and representative responses. |
| **O3** | **NFR1:** Keep responses within the agreed latency target. | **Response Latency:** End-to-end p90 latency <3 seconds. | Complete query-response pipeline; timing instrumentation. | **Pending:** Latency measurements and calculated p90 for the defined workload. |
| **O3** | **NFR2:** Ensure answers are factually consistent with approved documents. | **Answer Correctness:** ≥80% correct responses on a curated evaluation set. | Retrieval and document-grounded generation. | **Pending:** Scored evaluation set with reference answers and correctness calculation. |
| **O2, O3** | **NFR3:** Keep inference cost within the project budget. | **Criterion derived from requirement:** <US$0.50 per 100 queries; currently an illustrative budget. | Model/API usage tracking and cost calculation. | **Pending:** Usage records and calculated cost per 100 queries. |
| **O1, O2, O3** | **NFR4:** Incorporate approved source updates without rebuilding unrelated components. | **Criterion derived from requirement:** Document update time <10 minutes. | Document ingestion and ChromaDB update process. | **Pending:** Timed document-update test and verification that revised information is retrieved. |
| **O3** | **RAI1:** Keep performance differences across relevant student groups within tolerance. | **Criterion derived from requirement:** Absolute correctness-rate gap ≤10 percentage points. | Representative document coverage and stratified evaluation capability. | **Pending:** Group-level correctness scores and calculated gaps; faculty-based comparison where justified. |
| **O2, O3** | **RAI3:** Prevent student PII from being transmitted to external model APIs. | **Criterion derived from requirement:** Zero detected PII transmissions. | PII detection/removal before external API calls. | **Pending:** Privacy test results and inspection of outgoing API payloads. |