# Evaluation Criteria — EduAdvisor

| Objective / Requirement ID | Evaluation Criterion | Capability Bucket | Measurement Method | Metric | Threshold | User / Business Outcome |
|---|---|---|---|---|---|---|
| O3 / NFR2 | Answer Correctness | Domain-specific capability | Evaluate a defined set of supported academic queries using a rubric. | Correct response rate | ≥ 80% | Users receive sufficiently reliable answers for routine academic enquiries. |
| O1 / FR3 / RAI4 | Source Citation and Support | Instruction-following capability | Inspect document-grounded responses for citation presence and verify whether cited sources support the answer. | Citation presence rate; citation-source match rate | 100% presence; ≥ 95% match | Users can verify information against approved university sources. |
| O2 / RAI2 | Out-of-Scope Refusal | Instruction-following capability | Test the system with a defined safety/scope query set. | Refusal-and-redirect success rate | ≥ 95% | Reduces inappropriate advice outside the intended academic scope. |
| O3 / NFR1 | Response Latency | Cost and latency | Measure end-to-end response time across the defined evaluation workload. | p90 latency | < 3 s | Users receive sufficiently responsive interaction. |
| O1 / FR5 | Response Clarity | Generation capability | Assess response clarity using a simple defined rubric. | Clarity rubric score | Meets defined clarity criterion | Students can understand the academic information provided. |
