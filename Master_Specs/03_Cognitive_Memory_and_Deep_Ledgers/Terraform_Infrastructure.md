# ULTRA TERRAFORM: Infrastructure as Code Specifications

## Table of Contents
1.  [Global External App Load Balancer](#setting-up-a-global-external-application-load-balancer)
2.  [Serverless NEGs for Cloud Run](#3-cloud_run_and_negtf)
3.  [Identity Platform (Multi-Tenant GCIP)](#configuring-a-multi-tenant-google-cloud-identity-platform)
4.  [BigQuery Immutable Ledger](#1-the-immutable-deep_memory_ledger-in-google-bigquery)
5.  [Engineering Annotations](#engineers-notes)

## Global External App Load Balancer
Standardized process for routing traffic to Serverless Cloud Run services via NEGs.

### Resource Components
-   **Static IP:** `google_compute_global_address`
-   **SSL:** `google_compute_managed_ssl_certificate` (Auto-renewing)
-   **Backend:** `google_compute_backend_service` with `SERVERLESS` NEG.
-   **Routing:** `google_compute_url_map` with HTTP-to-HTTPS redirect.

## Identity Platform (Multi-Tenant GCIP)
Configuration for isolating users and projects within the "Swarm."

### Tenants & Claims
-   **Tenant Creation:** `google_identity_platform_tenant`
-   **Auth Providers:** Email/Password and social IDPs.
-   **Custom Claims:** Blocking Cloud Functions to inject `tenant_id` into JWTs for Firestore RLS.

## BigQuery Immutable Ledger
Creating the `deep_memory_ledger` for persistent agent introspection.

### Schema & Performance
-   **Partitioning:** Daily partitions on `timestamp`.
-   **Clustering:** `tenant_id`, `agent_id`.
-   **Security:** Row-Level Security (RLS) policies to enforce multi-tenancy at the data layer.

## Engineering Notes
> **Engineer's Note (Terraform):** Always set `deletion_protection = true` for the BigQuery ledger. This is the only immutable record of agent costs and decisions; its loss is a catastrophic failure of the Omnicron Codex.
>
> **Engineer's Note (Networking):** Serverless NEGs must be created in the same region as the Cloud Run service. Cross-region NEGs are not supported for serverless backends.

---
*Blueprint Version: 3.0.1 (Production)*
