# Empire Protocol: Operation Ouroboros (V3)

## Table of Contents
1. [Core Philosophy](#core-philosophy)
2. [Enterprise Identity Handshake](#enterprise-identity-handshake)
3. [Pillar A: The Headless Titan](#pillar-a-the-headless-titan)
4. [Pillar B: The Tri-Memory Ledger](#pillar-b-the-tri-memory-ledger)
5. [Pillar C: Mission Control Cockpit](#pillar-c-mission-control)
6. [Operation: Empire Build (Phase 1)](#operation-empire-build)
7. [Engineering Annotations](#engineers-notes)

## Core Philosophy
We are building an **Autonomous AI Holding Company**. The system must live 24/7 in the cloud, manage its own tools, and evolve autonomously.

## Enterprise Identity Handshake
Binding operations to Organization-level parameters:
- **Org ID:** 590284199463
- **Billing:** 01B0E2-0BB3A6-F520A2
- **Project:** project-255816db-f405-4b8b-b48
- **Region:** europe-west1 (Belgium)

## Pillar A: The Headless Titan
Service: `evo-architect-headless` on Cloud Run.
- **DNA:** Installs full toolbelt (Terraform, Maestro, Security, Context7, Superpowers).
- **The Ouroboros Loop:** Cloud Build triggers allow the agent to modify its own Dockerfile and redeploy itself.

## Pillar B: The Tri-Memory Ledger
- **Hot Memory:** Firestore Native for heartbeat tracking.
- **Deep Memory:** BigQuery `deep_memory_ledger` for persistent introspection.
- **Self-Optimization:** Automated ledger querying every 60 minutes.

## Pillar C: Mission Control
Service: `mission-control-dashboard` (Open WebUI).
- **Handshake:** Wired to `evo-gateway`.
- **Evolution Bridge:** Custom action for manual approval/rejection of "Wisdom Upgrades."

## Engineering Notes
> **Engineer's Note (DNA):** The "Ouroboros" name refers to the system's ability to "consume" its own logs and "re-create" its own source code. This is the definition of a Tier 1 Autonomous IaaS.
>
> **Engineer's Note (Approval):** The "Evolution Bridge" custom action is the critical human-in-the-loop safety valve. Never allow the Titan to merge code changes without this bridge's handshake during Phase 1.

---
*Protocol Version: 3.0.0 (Mandate Active)*
