# Genesis Script: Automated Cloud Orchestration

## Table of Contents
1.  [Overview](#overview)
2.  [Script Architecture](#script-architecture)
3.  [Orchestrator Logic (The Brain)](#orchestrator-logic)
4.  [Worker Logic (The Scanner)](#worker-logic)
5.  [Engineering Annotations](#engineers-notes)

## Overview
The Genesis Script is a "Giga-Block" command that provisions the entire AI Swarm on GCP, including IAM, Cloud Run services, and Firestore persistence.

## Script Architecture
The script performs the following sequence:
1.  **API Enablement:** Enables `aiplatform`, `run`, `firestore`, `cloudbuild`, and `discoveryengine`.
2.  **IAM Setup:** Creates the `evo-brain-sa` service account.
3.  **Brain Deployment:** Deploys a Node.js Express app to Cloud Run as the central router.
4.  **Scanner Deployment:** Deploys a containerized background job for market scanning.
5.  **Heartbeat Setup:** Configures Cloud Scheduler to trigger the scanner hourly.

## Orchestrator Logic
The "Brain" routes requests between specialized agents:
-   **ARCHITECT (Claude 4.6):** Deep coding and system design.
-   **SCANNER:** Real-time data tasks.
-   **CHAT (Gemini 3.1):** Standard conversational processing.

## Engineering Notes
> **Engineer's Note (Model Routing):** The Brain uses **Gemini 3.1 Pro** as the high-speed router to classify user intent before delegating heavy reasoning to **Claude 4.6 Sonnet**.
>
> **Engineer's Note (Persistence):** The Scanner job syncs results to Firestore, enabling the Brain to maintain a "Single Window" view of all autonomous activities without constant polling.

---
*Genesis Script Version: 1.0.0 (Giga-Block)*
