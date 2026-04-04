# Resilience Protocol: Automated Safety & Real-Time State

## Table of Contents
1.  [Automated Rollback System](#automated-rollback-system)
2.  [Hot Memory Architecture (Firestore)](#firestore-as-hot-memory)
3.  [Distributed Task Queue Implementation](#distributed-task-queue)
4.  [Engineering Annotations](#engineers-notes)

## Automated Rollback System
To ensure deployment safety, the system monitors new revisions and automatically reverts to stable versions if KPIs degrade.

### Implementation Chain
1.  **Cloud Monitoring:** Alert triggers on high 5xx error rates or P99 latency spikes.
2.  **Pub/Sub:** Transmits the alert to a handler.
3.  **Cloud Function:** Executes the rollback logic via Cloud Run Admin API.
4.  **Action:** Programs shifts 100% of traffic back to the last known stable revision.

### Required IAM Permissions
-   `roles/run.admin` (or custom role with `run.services.get` and `run.services.update`).
-   `roles/pubsub.publisher` for Monitoring.

## Firestore as Hot Memory
Firestore serves as the system's real-time "nervous system" for tracking agent status and shared state.

### Data Model
-   **`agents` collection:** Tracks real-time status (idle, busy, error) and heartbeats.
-   **`tasks` collection:** A distributed queue for inter-agent work allocation.
-   **`sessions` collection:** Ephemeral state for multi-step workflows.

## Distributed Task Queue
The queue ensures atomic task assignment through Firestore transactions.

### Workflow
1.  **Creation:** Orchestrator creates a `pending` task.
2.  **Discovery:** Idle agents query for `pending` tasks.
3.  **Assignment:** Agent uses a **Transaction** to set `status: assigned` and `assigneeAgentId: [ID]`.
4.  **Completion:** Agent writes `result` and sets `status: completed`.

## Engineering Notes
> **Engineer's Note (Firestore):** Use **Time-to-Live (TTL)** policies on the `sessions` collection to automatically prune stale data and manage storage costs.
>
> **Engineer's Note (Rollbacks):** Always sort revisions by `create_time` descending. The `revisions[0]` is typically the faulty one, and `revisions[1]` is the target rollback candidate.

---
*Blueprint Version: 3.0.1 (Production)*
