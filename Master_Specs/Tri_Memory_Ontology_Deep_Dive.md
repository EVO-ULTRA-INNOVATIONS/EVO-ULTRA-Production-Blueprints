# Tri-Memory Ontology: Data Architecture Deep-Dive

## Table of Contents
1.  [The Memory Hierarchy](#the-memory-hierarchy)
2.  [L0 (Hot Memory): Firestore Native](#l0-hot-memory-firestore-native)
3.  [L1 (Deep Memory): BigQuery Immutable Ledger](#l1-deep-memory-bigquery-immutable-ledger)
4.  [L2 (Cached Context): Vertex AI Context Caching](#l2-cached-context-vertex-ai-context-caching)
5.  [Multi-Tenant Data Isolation](#multi-tenant-data-isolation)
6.  [Engineering Annotations](#engineers-notes)

## The Memory Hierarchy
EVO ULTRA employs a tiered memory architecture to balance latency, persistence, and cost. This "Cortex" ensures that agents retain context across sessions and learn from past operations.

## L0 (Hot Memory): Firestore Native
-   **Purpose:** Real-time state tracking and inter-agent coordination.
-   **Collections:**
    -   `agents`: Live status, heartbeats, and capability mapping.
    -   `tasks`: Distributed queue for workload assignment.
    -   `sessions`: Ephemeral state for active user interactions.
-   **Feature:** Vector Search enabled for semantic retrieval of short-term memories.

## L1 (Deep Memory): BigQuery Immutable Ledger
-   **Purpose:** Long-term audit trails, financial performance tracking, and evolutionary training data.
-   **Schema:** `event_id`, `timestamp`, `tenant_id`, `agent_id`, `action_name`, `execution_time_ms`, `cost_usd`, `is_error`, `source_code_reference`.
-   **Optimization:** Partitioned by `timestamp` (daily), Clustered by `tenant_id` and `agent_id`.

## L2 (Cached Context): Vertex AI Context Caching
-   **Purpose:** Persistent storage of massive system instructions and enterprise rules.
-   **Benefit:** Reduces token burn burn for high-frequency agent calls by up to 90%.
-   **Trigger:** Automatically refreshed when the Architect Agent Merges a "Wisdom Upgrade" to the core system instructions.

## Multi-Tenant Data Isolation
-   **GCIP Handshake:** Users authenticate and receive a `tenant_id` in their JWT.
-   **Firestore Rules:** `allow read, write: if request.auth.token.tenant_id == resource.data.tenant_id`.
-   **BigQuery RLS:** `CREATE ROW ACCESS POLICY` filtering rows by the session's tenant ID.

## Engineering Notes
> **Engineer's Note (Memory Drift):** Periodically run a "Garbage Collection" job on L0 sessions to move completed interaction summaries to L1 and prune the Firestore database.
>
> **Engineer's Note (Scalability):** Use Firestore sub-collections (`tenants/{tenantId}/agents/{agentId}`) to ensure that query results are naturally restricted to the tenant boundary at the root level.

---
*Ontology Version: 3.1.0 (Production)*
