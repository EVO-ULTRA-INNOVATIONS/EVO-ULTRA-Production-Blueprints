# Simultaneous Full-Arsenal FinOps: Three-Tier Credit Strategy

## Table of Contents
1.  [Objective](#objective)
2.  [The Credit Tiers](#the-credit-tiers)
3.  [The Dual-Project Isolation](#dual-project-isolation)
4.  [Burn-Down Optimization](#burn-down-optimization)
5.  [Circuit Breaker Mechanism](#circuit-breaker-mechanism)
6.  [Engineering Annotations](#engineers-notes)

## Objective
Ensure self-sustaining cash flow before credit depletion by burning available Google Cloud credits in the most mathematically efficient order.

## The Credit Tiers
-   **Tier 1: $1,000 Vertex AI Promotion:** Specifically for Agent Builder and Search. Must be used for all RAG and conversational grounding.
-   **Tier 2: $300 General Cloud Trial:** For direct Gemini 3.1 Pro API calls, Cloud Run, Firestore, and BigQuery.
-   **Tier 3: Efficiency Credits:** Leveraging the Firebase Blaze Plan and Enterprise subscription to extend the runway of Tier 2 credits.

## The Dual-Project Isolation
To prevent credit "bleeding" and ensure isolation:
-   **Project A (Cognitive Core):** Hosts Vertex AI Agent Builder and Vertex Search. Restricted to Tier 1 credit consumption.
-   **Project B (Execution Engine):** Hosts Cloud Run workers, Firestore state, and BigQuery ledgers. Primarily consumes Tier 2/3 credits.

## Burn-Down Optimization
1.  **Grounding First:** All queries must hit the Agent Builder application first. If the managed response is sufficient, the task is complete (Tier 1 burn).
2.  **Selective Escalation:** Only delegate to raw Gemini models (Tier 2 burn) for tasks requiring deep reasoning or custom code generation that exceeds Agent Builder's scope.

## Circuit Breaker Mechanism
-   **Threshold:** 95% budget depletion in either project.
-   **Action:** A Cloud Function triggered by Pub/Sub budget alerts sets a global `halt_operations: true` flag in the Firestore `system_config` collection.
-   **Recovery:** Manual reset required after credit renewal or revenue injection.

## Engineering Notes
> **Engineer's Note (Isolation):** Mixing promotional GenAI credits with general compute leads to "FinOps Drift," where expensive AI tokens are wasted on low-value container uptime. Always use the Dual-Project Terraform configuration.
>
> **Engineer's Note (Monitoring):** Use the `gcloud beta billing budgets` command during the "Master Scan" to programmatically verify the current remaining balance of each credit tier.

---
*FinOps Version: 2.5.0 (Definitive)*
