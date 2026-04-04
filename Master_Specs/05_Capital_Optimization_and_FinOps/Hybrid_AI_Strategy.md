# Hybrid AI Strategy: Agent Builder vs. Raw Models

## Table of Contents
1.  [Strategic Comparison](#strategic-comparison)
2.  [Credit Optimization Strategy](#maximizing-promotional-credits)
3.  [Architectural Patterns](#architectural-patterns)
4.  [Workflow Integration Walkthrough](#integrating-with-cloud-workflows)
5.  [Engineering Annotations](#engineers-notes)

## Strategic Comparison
Building a hybrid system requires choosing the right tool for each task.

| Feature | Vertex AI Agent Builder | Direct Gemini API Calls |
| :--- | :--- | :--- |
| **Complexity** | Low/Medium (Managed) | High (Custom) |
| **Grounding** | Managed RAG (Search) | Manual RAG Implementation |
| **Pricing** | Per 1,000 Queries | Per 1,000 Tokens |
| **Control** | Standardized | Full Flexibility |

## Maximizing Promotional Credits
EVO ULTRA prioritizes Vertex AI Agent Builder for initial data-grounding and conversational tasks to maximize the **$1,000 GenAI App Builder credits**.

### The "Managed First" Pattern
1.  **Ingestion:** Connect enterprise data to Vertex AI Search.
2.  **Conversation:** Use Vertex AI Conversation for multi-turn flows.
3.  **Escalation:** Only call raw Gemini models via Cloud Functions for tasks requiring custom logic or advanced reasoning not supported by the managed agent.

## Integrating with Cloud Workflows
Cloud Workflows orchestrates the interaction between the user interface and the Agent Builder application.

### API Configuration
-   **Endpoint:** `detectIntent` (Dialogflow CX based).
-   **Authentication:** Service Account with `roles/aiplatform.reasoningEngine.invoker`.
-   **Method:** HTTP POST with OIDC/OAuth2 tokens.

## Engineering Notes
> **Engineer's Note (Cost):** Standard Gemini API calls are *not* covered by the GenAI App Builder credits. Always check the `responseMessages` from Agent Builder first; if valid, skip the raw model call to preserve budget.
>
> **Engineer's Note (RAG):** Vertex AI Search handles chunking and embeddings automatically. For custom RAG using raw models, use **Vertex AI Vector Search** to maintain performance at scale.

---
*Blueprint Version: 3.0.1 (Production)*
