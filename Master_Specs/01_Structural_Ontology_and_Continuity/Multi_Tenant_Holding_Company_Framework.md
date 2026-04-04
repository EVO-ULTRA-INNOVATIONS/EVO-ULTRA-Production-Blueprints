# AI Holding Company Framework: Multi-Tenant IaaS

## Table of Contents
1.  [Core Vision](#core-vision)
2.  [The Holding Company Mandate](#holding-company-mandate)
3.  [Architectural Multi-Tenancy](#architectural-multi-tenancy)
4.  [Financial & Operational Record Keeping](#financial-record-keeping)
5.  [Engineering Annotations](#engineers-notes)

## Core Vision
EVO ULTRA is not designed as a single project but as a foundational **Platform-as-a-Service (PaaS)** for an Autonomous AI Holding Company. The system provisions infrastructure for multiple, distinct AI-driven business ventures (Business Units).

## Holding Company Mandate
-   **Scalability:** The platform must support the rapid launch of new ventures with zero-entry cost.
-   **Isolation:** Each venture operates in its own containerized or project-level environment to prevent cross-contamination.
-   **Centralized Oversight:** A single "Mission Control" interface manages all child business units.

## Architectural Multi-Tenancy
The infrastructure enforces tenancy at three levels:
1.  **Identity Layer:** Google Cloud Identity Platform (GCIP) partitions users by `tenant_id`.
2.  **Logic Layer:** Worker agents are tagged with `business_unit` headers in all API calls.
3.  **Data Layer:** Firestore sub-collections and BigQuery Row-Level Security (RLS) filter data based on session tokens.

## Financial Record Keeping
The BigQuery `deep_memory_ledger` is the source of truth for the company's performance.
-   **Partitioning:** Data is partitioned by `business_unit` and `timestamp`.
-   **Metrics:** Tracking of unit-specific token burn, compute cost, and ROI.

## Engineering Notes
> **Engineer's Note (Organization):** Use the `thevintagevaultglobal-org` (ID: 590284199463) as the root parent. All business units should be projects created under this organization to inherit Enterprise-level quotas.
>
> **Engineer's Note (Isolation):** When a new venture is spun up, the Architect Agent must automatically provision a new `tenant_id` in GCIP and update the load balancer's URL map to route the unit's subdomain to its dedicated worker swarm.

---
*Framework Version: 3.0.0 (Empire Grade)*
