# EVO ULTRA: The Comprehensive Master Plan

## Table of Contents
1.  [The Strategy](#architecture--strategy)
2.  [The EVO ULTRA Anatomy](#the-evo-ultra-anatomy)
3.  [Roadmap: Command Center & Quotas](#phase-1-the-command-center--quotas)
4.  [Roadmap: Deploying 'The Brain'](#phase-2-deploying-the-brain)
5.  [Roadmap: The Evolution Loop](#phase-4-the-evolution-loop)
6.  [Final Storage Review](#final-storage-architecture-review)
7.  [Engineering Annotations](#engineers-notes)

## Architecture & Strategy
To escape the limits of consumer-grade AI studios, EVO ULTRA migrates from a SaaS subscription model to a full Enterprise PaaS environment on Google Cloud (Vertex AI).

## The EVO ULTRA Anatomy
-   **The Interface (Single Window):** Firebase (Vertex AI for Firebase SDK, App Check, Genkit).
-   **The Brain (Orchestrator):** Node.js logic on Cloud Run acting as the request manager and prompt router.
-   **The Muscle (Agents):** Gemini 3.1 Pro and Claude 3.5/4.6 Sonnet via Vertex AI Model Garden.
-   **The Body (Passive Workers):** Cloud Run Jobs running 24/7 scanning, dropshipping, and investing tasks.
-   **External Cortex (Memory):** Firestore (Active Hot Memory) and Cloud Storage (Archives).
-   **Self-Evolution Engine:** Cloud Source Repositories + Cloud Build for autonomous code rewriting.

## Phase 1: The Command Center & Quotas
1.  **Launch Cloud Shell:** Provision a 5GB Linux environment for initialization.
2.  **Quota Increase:** Request 60 RPM for Gemini 1.5/3.1 Pro via IAM & Admin.
3.  **Enable Model Garden:** Activate Claude 3.5/4.6 Sonnet endpoints.

## Phase 2: Deploying 'The Brain'
The "Magic Block" deployment provisions APIs and creates the orchestrator identity.
-   **Logic:** Node.js app routing based on request complexity (ARCHITECT vs. CHAT).
-   **Automation:** Scripted deployment via `gcloud run deploy`.

## Phase 4: The Evolution Loop
The system is designed to "reincarnate" itself by refactoring its own worker scripts.
-   **Workflow:** Architect Agent writes new code -> Commits to Git -> Cloud Build triggers -> New worker revision deploys.

## Engineering Notes
> **Engineer's Note (Hardware):** This plan is designed to be executable from any device, including an S20 smartphone, by leveraging the Google Cloud Shell Editor as a mobile-optimized IDE.
>
> **Engineer's Note (Model Choice):** Use **Claude 4.6 Sonnet** for the "Architect" role as it is currently the global leader in coding reasoning and autonomous self-evolution logic.

---
*Document Version: 11.0.0 (Unified Build)*
