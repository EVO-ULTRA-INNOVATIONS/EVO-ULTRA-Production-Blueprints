# Global Deep-Scan: Zero-Cost Cloud Trajectories

## Table of Contents
1.  [Analysis of Operational Freedom](#analysis-of-operational-freedom-acceptable-use-policies)
2.  [Trajectory 1: Google Cloud Platform (GCP)](#trajectory-1-google-cloud-platform-gcp-billing-and-credits)
3.  [Trajectory 2: Oracle 'Always Free' Titan](#trajectory-2-oracle-always-free-arm-titan)
4.  [Trajectory 3: Microsoft Founders Hub](#trajectory-3-the-startup-lottery-hyperscaler-accelerators)
5.  [Trajectory 4: Vultr Post-Pay Tactical](#trajectory-4-neocloud-identity-only-onboarding--post-pay-models)
6.  [Trajectory 5: Fly.io Persistent UI](#trajectory-5-ui-cockpit-on-free-tier-hosts)
7.  [The Sovereign Power Matrix](#sovereign-power-matrix)
8.  [Engineering Annotations](#engineers-notes)

## Analysis of Operational Freedom (AUP)
-   **Web Scraping:** Permissive on Oracle (if non-abusive), explicitly prohibited for AI services on Azure, and restricted on Vultr.
-   **Self-Modification:** Generally permitted as long as the outcomes (e.g., malware) do not violate AUP.
-   **Crypto-Logic:** Blockchain nodes are permitted; direct cryptocurrency mining is universally banned on free tiers.

## Trajectory 2: Oracle 'Always Free' ARM Titan
The maximum-specification free server identified.
-   **Specs:** 4 OCPUs (ARM Ampere), 24GB RAM, 200GB Boot Volume.
-   **Strategy:** Upgrade to Pay-As-You-Go (PAYG) to bypass capacity limits while remaining within free usage bounds.

## Trajectory 3: Microsoft Founders Hub
The most strategic long-term play for pre-revenue ideas.
-   **Benefit:** $1,000 to $150,000 in Azure credits.
-   **Advantage:** Mature platform with less arbitrary AUP enforcement compared to Oracle.

## The Sovereign Power Matrix
| Trajectory | Financial Zero-Entry | Sovereignty | Persistence | Overall Rank |
| :--- | :--- | :--- | :--- | :--- |
| **Oracle ARM** | Excellent | Good | Good | **1** |
| **MS Founders Hub** | Excellent | Good | Excellent | **2** |
| **Vultr Promo** | Good | Fair | Poor | **3** |
| **GCP Free Trial** | Good | Good | Fair | **4** |

## Engineering Notes
> **Engineer's Note (Persistence):** Fly.io is the only identified free-tier host that allows disabling "auto-stop" for 24/7 UI availability, though its 256MB RAM limit is extremely tight for Open WebUI.
>
> **Engineer's Note (Provisioning):** To secure an Oracle ARM instance in high-demand regions, use a JavaScript automation snippet in the browser console to auto-retry the "Create" button every 60 seconds.

---
*Deep-Scan Version: 2026.Q1*
