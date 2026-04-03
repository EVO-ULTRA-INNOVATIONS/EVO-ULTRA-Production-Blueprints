# Deep Research Blueprint: Global Load Balancing & Identity

## Table of Contents
1. [Terraform: Global External App Load Balancer](#global-external-app-load-balancer)
2. [Serverless NEGs for Cloud Run](#serverless-negs)
3. [Identity Platform: Multi-Tenant Configuration](#multi-tenant-identity-platform)
4. [Row-Level Security (RLS) Policies](#row-level-security)
5. [Engineering Annotations](#engineers-notes)

## Global External App Load Balancer
A detailed guide for routing traffic to Cloud Run using Google Cloud's global infrastructure.

### Architectural Flow
`[Client] -> [Global Forwarding Rule] -> [Target Proxy] -> [URL Map] -> [Backend Service] -> [Serverless NEG] -> [Cloud Run]`

### Terraform Configuration
- **Static IP:** `google_compute_global_address`
- **SSL:** `google_compute_managed_ssl_certificate`
- **Redirects:** `google_compute_url_map` (HTTP to HTTPS)

## Serverless NEGs
The critical link between global load balancing and regional serverless compute.
- **Requirement:** Must be in the same region as the Cloud Run service.
- **Ingress:** `INGRESS_TRAFFIC_INTERNAL_LOAD_BALANCER` recommended for security.

## Multi-Tenant Identity Platform
Process for configuring distinct user pools (tenants) using GCIP.
- **Authentication:** Enabling Email/Password and Google Sign-In.
- **Custom Claims:** Utilizing Blocking Cloud Functions to inject `tenant_id` into JWTs.

## Row-Level Security
Enforcing data isolation at the BigQuery level using user session claims.
- **SQL Policy:** `CREATE ROW ACCESS POLICY` filtering by `SESSION_USER()`.

## Engineering Notes
> **Engineer's Note (Networking):** Load balancer propagation can take up to 20 minutes for SSL certificates to provision. Do not assume immediate availability after `terraform apply`.
>
> **Engineer's Note (Security):** Row-Level Security is the final line of defense. Even if an agent is compromised, it cannot query data outside its assigned `tenant_id` at the database engine level.

---
*Blueprint Version: 3.0.1 (Production)*
