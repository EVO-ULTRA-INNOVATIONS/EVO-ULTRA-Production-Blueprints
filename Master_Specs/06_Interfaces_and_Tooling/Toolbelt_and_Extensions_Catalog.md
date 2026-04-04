# Toolbelt & Extensions Catalog: AI Build Optimization

## Table of Contents
1.  [Overview](#overview)
2.  [Top Extensions for Gemini CLI](#top-extensions-for-gemini-cli)
3.  [Specialized Build Tools](#specialized-build-tools)
4.  [Integration Roadmap](#integration-roadmap)
5.  [Engineering Annotations](#engineers-notes)

## Overview
A catalog of verified Gemini CLI extensions and ADK-compatible tools identified during the "Global Deep-Scan" to accelerate the build of the Mission Control interface and worker swarm.

## Top Extensions for Gemini CLI
-   **`adk-docs-ext`:** Provides Gemini with up-to-date information about the Agent Development Kit via `llms.txt`.
-   **`firebase-genkit-mcp`:** Managed service interface for Genkit flows and dashboarding.
-   **`gcloud-monitoring-alerts`:** Custom extension for pipeing Cloud Monitoring signals directly into the CLI brain.
-   **`terraform-plan-validator`:** Automated audit tool for verifying Terraform scripts before `apply`.

## Specialized Build Tools
-   **Genkit:** The primary framework for building production AI features in Node.js/TypeScript.
-   **App Check:** Security layer for the Mission Control frontend.
-   **Secret Manager SDK:** For dynamic fetching of Git and API credentials at runtime.

## Engineering Notes
> **Engineer's Note (ADK):** Use the `adk-docs-ext` whenever refactoring worker agents. This ensures the CLI uses the latest enterprise patterns for BigQuery streaming and Cloud Run Jobs.
>
> **Engineer's Note (Security):** All new extensions must be validated against the `terraform-plan-validator` to ensure they do not accidentally open public firewall ports.

---
*Catalog Version: 5.8.9 (Enterprise)*
