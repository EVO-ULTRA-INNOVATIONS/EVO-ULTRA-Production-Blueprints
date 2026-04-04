# Mission Control UI: Frontend Execution Strategies

## Table of Contents
1.  [Objective](#objective)
2.  [Plan A: The "Pure Enterprise" Build](#plan-a-the-pure-enterprise-build)
3.  [Plan B: The "Modular Dash" (Recommended)](#plan-b-the-modular-dash)
4.  [Plan C: The "Mobile Cockpit" Rapid Start](#plan-c-the-mobile-cockpit-rapid-start)
5.  [Core Components](#core-components)
6.  [Engineering Annotations](#engineers-notes)

## Objective
Establish a persistent 'Single Window' interface for EVO ULTRA orchestration, capable of running 24/7 and accessible from any device.

## Plan A: The "Pure Enterprise" Build
-   **Stack:** Next.js 15, Tailwind CSS, Firebase Auth.
-   **Deployment:** Cloud Run (Global LB).
-   **Pros:** Total control, professional aesthetics, deep Genkit integration.
-   **Cons:** Highest development time (3-5 days for MVP).

## Plan B: The "Modular Dash" (Recommended)
-   **Stack:** Streamlit or Reflex (Python-based UI) + Node.js API.
-   **Deployment:** Cloud Run (Single Instance).
-   **Pros:** Blazing fast development, native support for data visualization (BigQuery).
-   **Cons:** Limited layout flexibility compared to React.

## Plan C: The "Mobile Cockpit" Rapid Start
-   **Stack:** Open WebUI (Dockerized).
-   **Deployment:** Cloud Run or GCE.
-   **Pros:** Instant 24/7 UI, mobile-native responsiveness, built-in model switching.
-   **Cons:** Requires custom "Functions" or "Actions" to pipe into our orchestrator.

## Core Components
-   **Single Window:** Firebase SDK for real-time dashboard updates.
-   **Identity:** Google Identity Platform for secure multi-tenant access.
-   **Command Input:** Voice-to-text integration for smartphone-based commanding.

## Engineering Notes
> **Engineer's Note (UI Choice):** Plan C is the fastest route to "Production Status," while Plan A is the target for the "EVO ULTRA GA" release.
>
> **Engineer's Note (Firebase):** Ensure **Firebase App Check** is enabled to prevent unauthorized third-party scripts from consuming our £961 credits via the frontend API.

---
*Blueprint Version: 3.0.1 (Frontend Design)*
