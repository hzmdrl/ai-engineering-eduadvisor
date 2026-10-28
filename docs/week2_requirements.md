
## Section 1
## Functional Requirements — EduAdvisor

**Version:** 1.0

| # | Requirement — The system SHALL | Scope Boundary — SHALL NOT (where relevant) |
|---|---|---|
| **FR1** | Answer questions about course codes, titles, credits, and descriptions from the current course catalogue. | Invent course codes or course details that are not supported by the source documents. |
| **FR2** | Answer questions about prerequisite requirements for courses listed in the catalogue. | Decide whether a student should receive a prerequisite waiver. |
| **FR3** | Provide a source reference for answers based on university documents. | Present unsupported information as if it came from an approved source. |
| **FR4** | Decline queries that fall outside the defined academic advising scope and provide an appropriate redirect. | Provide medical, legal, financial, or mental health advice. |
| **FR5** | Present answers in clear language appropriate for undergraduate students. | — |


## Section 2
## Non-Functional Requirements — EduAdvisor

**Version:** 1.0

| # | Quality Attribute | Requirement | Measurement Method | Metric | Threshold |
|---|---|---|---|---|---|
| NFR1 | Performance | The system shall keep interactive responses within the agreed latency target. | Measure end-to-end latency on a defined test workload | p90 latency | < 3,000 ms |
| NFR2 | Correctness | Answers shall be factually consistent with approved source documents. | Score a curated evaluation set using a defined rubric. | Correct response rate (%) | ≥ 80% |
| NFR3 | Cost | Inference cost shall remain within the project budget. |Record model/API usage over the evaluation workload. | Cost per 100 queries. | < US$0.50 per 100 queries (illustrative) |
| NFR4 | Maintainability | Approved source updates shall be incorporated without rebuilding unrelated components. | Run a controlled document-update test. | Update time | < 10 min |


## Section 3
## Responsible AI Requirements — EduAdvisor

**Version:** 1.0

| # | Responsible AI Risk | Requirement | Measurement Method | Metric | Threshold |
|---|---|---|---|---|---|
| RAI1 | Fairness | System performance shall not differ beyond the agreed tolerance across relevant student groups. | Evaluate a stratified test set and compare correctness rates across justified student groups. | Absolute correctness-rate gap between groups | ≤ 10 percentage points |
| RAI2 | Safety / Scope | The system shall refuse out-of-scope queries and redirect users appropriately. | Run a defined safety/scope test set containing at least 20 out-of-scope queries. | Refusal-and-redirect success rate | ≥ 95% |
| RAI3 | Privacy | The system shall not transmit student PII to external model APIs. | Run privacy test cases and inspect outgoing model/API payloads. | Number of detected PII transmissions | 0 |
| RAI4 | Transparency / Grounding | The system shall provide a verifiable source reference for document-grounded answers and indicate when sufficient supporting evidence cannot be found. | Evaluate document-grounded responses for citation presence and whether the cited source supports the answer | Citation presence rate; citation-source match rate | 100% citation presence; ≥95% citation-source match |


