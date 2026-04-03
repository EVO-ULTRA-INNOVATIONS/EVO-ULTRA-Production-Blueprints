# Headless Titan DNA: Containerized Architect Agent

## Table of Contents
1.  [Objective](#objective)
2.  [Container Specifications](#container-specifications)
3.  [The Self-Tooling Swarm Loop](#the-self-tooling-swarm-loop)
4.  [Deployment Configuration](#deployment-configuration)
5.  [Engineering Annotations](#engineers-notes)

## Objective
Establish a persistent, headless version of the Gemini CLI running 24/7 on Cloud Run to act as the autonomous "Executive Brain" of the holding company.

## Container Specifications
-   **Base Image:** `node:20-slim`
-   **Memory:** 8GiB minimum (required for heavy Docker builds and Terraform analysis).
-   **Toolbelt (The DNA):**
    -   `@hashicorp/terraform`
    -   `@google-cloud/functions-framework`
    -   `@gemini-cli-extensions/security`
    -   `@josstei/maestro-gemini`
    -   `@obra/superpowers`

## The Self-Tooling Swarm Loop
The Headless Titan evolves through a GitOps cycle:
1.  **Identify Need:** Titan analyzes the `deep_memory_ledger` and discovers a missing capability.
2.  **Tool Search:** Titan searches the global registry or web for a new MCP server or extension.
3.  **DNA Modification:** Titan modifies its own `Dockerfile` or `package.json` to include the new tool.
4.  **Commit & Push:** Titan commits the change to its own Git repository.
5.  **Redeploy:** Cloud Build detects the push, builds the new "DNA" image, and redeploys the Headless Titan revision.

## Deployment Configuration
-   **Service Name:** `evo-architect-headless`
-   **Platform:** Cloud Run
-   **Auth:** Service Account with `roles/owner` (restricted to the organization boundary).
-   **Scheduler:** Triggered every 60 minutes via Cloud Scheduler to perform "Wisdom Upgrades."

## Engineering Notes
> **Engineer's Note (Persistance):** Ephemeral containers lose local storage. The Titan must mount a **Cloud Storage FUSE** volume or use Firestore to store its "State Map" between container restarts.
>
> **Engineer's Note (Recursion):** To prevent infinite "Tooling Loops," the Titan is restricted to one self-modification per 24 hours unless a high-priority "System Override" is detected in the ledger.

---
*DNA Version: 3.0.0 (Sentient Grade)*
