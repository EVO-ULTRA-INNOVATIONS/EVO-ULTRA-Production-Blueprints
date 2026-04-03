# Smooth Transition Protocol: SaaS to Enterprise PaaS

## Table of Contents
1.  [Objective](#objective)
2.  [The "Modular Extraction" Path](#the-modular-extraction-path)
3.  [The Genesis Script (v2.0)](#the-genesis-script-v20)
4.  [Core Implementation: The Brain (index.js)](#core-implementation-the-brain)
5.  [Core Implementation: The Muscle (main.py)](#core-implementation-the-muscle)
6.  [Engineering Annotations](#engineers-notes)

## Objective
Seamlessly migrate the EVO ULTRA brain from Google AI Studio (sandbox) to Vertex AI Enterprise (production) without disrupting the existing logic flow.

## The "Modular Extraction" Path
Instead of a "force merge" of disparate codebases, we use a staged approach:
1.  **Logic Hardening:** Use remaining AI Studio tokens to finalize perfect code snippets.
2.  **Staging:** Write all `index.js`, `main.py`, and `Dockerfile` files to a local staging folder.
3.  **One-Click Deployment:** Execute the `genesis.sh` script to provision and deploy the entire swarm.

## The Genesis Script (v2.0)
The script automates the following:
-   API Handshake (Enabling 10+ GCP services).
-   Service Account creation with Owner/Editor roles.
-   Project Project configuration for Billing and Identity.
-   Direct deployment of the Brain and Workers to Cloud Run.

## Core Implementation: The Brain
The Node.js Orchestrator handles:
-   **Routing:** Analyzing user prompts to determine if they require ARCHITECT (coding), SCANNER (live tasks), or CHAT (generic) agents.
-   **Memory:** Interfacing with Firestore for real-time state.
-   **Logging:** Syncing every decision to the BigQuery `operational_ledger`.

## Engineering Notes
> **Engineer's Note (API Safety):** The "Smooth Transition" depends on enabling the **Service Networking API** first. Without it, private agent-to-agent communication via VPC will fail.
>
> **Engineer's Note (Cost Efficiency):** By moving from AI Studio to Vertex AI, we stop using personal API keys and start burning the £961 Enterprise credits, saving approximately £25/month in personal out-of-pocket costs.

---
*Protocol Version: 2.0.0 (Staging Ready)*
