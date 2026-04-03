# Genesis Day Protocol: Hyper-Acceleration via Gemini CLI

## Table of Contents
1.  [Objective](#objective)
2.  [The "Master Prompt" Strategy](#the-master-prompt-strategy)
3.  [Genesis Day Workflow (0-4 Hours)](#genesis-day-workflow)
4.  [Autonomous Self-Correction Loop](#autonomous-self-correction)
5.  [Engineering Annotations](#engineers-notes)

## Objective
Reduce the infrastructure deployment timeline from weeks to hours by leveraging the Gemini CLI as an active, executive agent within the Google Cloud Shell.

## The "Master Prompt" Strategy
The "Genesis Day" begins with a single, high-density Master Prompt given to the Gemini CLI. This prompt instructs the agent to:
1.  **Authorize:** Authenticate with the Organization-level owner token.
2.  **Scan:** Execute the "Master Scan" to discover effective quotas.
3.  **Provision:** Write and apply Terraform for the dual-project architecture.
4.  **Deploy:** Initialize Cloud Run services and Firebase dashboard.
5.  **Validate:** Run end-to-end health checks across the Tri-Memory ontology.

## Genesis Day Workflow
-   **Hour 0: Initialization:** Enable APIs and create the core service accounts.
-   **Hour 1: Quota Mapping:** Discover "Ghost Parameters" and configure safety thresholds.
-   **Hour 2: Infrastructure:** `terraform apply` for Projects A and B.
-   **Hour 3: DNA Injection:** Deploy the Headless Titan and Mission Control UI.
-   **Hour 4: Activation:** Wake up the worker swarms and begin live scanning.

## Autonomous Self-Correction
The CLI agent is instructed to operate in a loop:
-   **Identify Failure:** Capture error logs from `gcloud` or `terraform`.
-   **Reason:** Consult the `adk-docs-ext` or `@upstash/context7` for the fix.
-   **Act:** Modify code/config and retry the operation.
-   **Report:** Log the outcome to the `deep_memory_ledger`.

## Engineering Notes
> **Engineer's Note (Acceleration):** Do not attempt to use the Cloud Console UI during Genesis Day. The latency of manual clicks is the primary bottleneck. The CLI agent operates 10x faster than a human operator.
>
> **Engineer's Note (Safety):** The "Master Prompt" must include a "Budget Gate." The agent is prohibited from creating any resource that would exceed the $500 initial monthly budget without a manual CEO override.

---
*Protocol Version: 1.5.0 (Hyper-Drive)*
