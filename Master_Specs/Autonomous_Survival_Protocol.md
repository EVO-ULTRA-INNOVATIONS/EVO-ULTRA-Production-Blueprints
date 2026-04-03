# Autonomous Survival Protocol: Resilience & Continuity

## Table of Contents
1.  [Objective](#objective)
2.  [Quota-Aware Throttling (Survival)](#quota-aware-throttling)
3.  [Absolute Continuity (Pillar 5)](#absolute-continuity--state-preservation)
4.  [Self-Correction Loop](#self-correction--rollback)
5.  [State Artifact Mapping](#state-artifact-mapping)
6.  [Engineering Annotations](#engineers-notes)

## Objective
Ensure the EVO ULTRA swarm remains operational 24/7 despite platform constraints, network disconnections, or faulty autonomous code modifications.

## Quota-Aware Throttling
-   **The Mechanism:** A specialized Cloud Function monitors the "Effective Quotas" discovered during the Genesis Day scan.
-   **Action:** Dynamically adjusts the `max-concurrency` and `max-instances` of the Cloud Run worker agents via the Admin API.
-   **Threshold:** System operates at a maximum of 80% of the identified cap to prevent 429 (Too Many Requests) cascades.

## Absolute Continuity & State Preservation
The system must survive "Cloud Shell Timeout" or user disconnection.
-   **State Map:** A persistent JSON artifact on disk and in Firestore tracking every file created, script run, and API enabled.
-   **Recovery Protocol:** Upon reconnection, the "Wake Up and Resume" command triggers a comparison between the State Map and the live GCP project status to identify and bridge gaps.

## Self-Correction Loop
-   **Red Teaming:** The `@gemini-cli-extensions/security` tool audits all agent-generated code before deployment.
-   **Automated Rollback:** If a new revision produces >5% error rate (5xx), Cloud Monitoring triggers an instant revert to the previous stable revision via Pub/Sub.

## State Artifact Mapping
Every action must be logged:
1.  **Memory:** Encoded into the `deep_memory_ledger`.
2.  **Disk:** Updated in the local `state_map.json`.
3.  **Context:** Appended to the persistent `GEMINI.md`.

## Engineering Notes
> **Engineer's Note (Stability):** Never use "LATEST" tags for worker containers. Always deploy with specific, immutable SHAs to ensure that rollbacks are deterministic and unaffected by registry overwrite events.
>
> **Engineer's Note (Continuity):** The State Map is the system's "Soul." If the map is corrupted, the system will enter a "Schizophrenic State," attempting to re-provision existing resources. Back up the State Map to a dedicated GCS bucket hourly.

---
*Protocol Version: 3.0.0 (Hardened)*
