# Quota & Limits Protocol: Pinpoint Perfect Mapping

## Table of Contents
1.  [Overview](#overview)
2.  [Phase 1: The "Ghost" Scan (Network & Egress)](#phase-1-the-ghost-scan-network--egress)
3.  [Phase 2: The "Brain" Scan (Vertex AI & Gemini)](#phase-2-the-brain-scan-vertex-ai--gemini)
4.  [Phase 3: The "Mega" Scan (Hidden Overrides)](#phase-3-the-mega-scan-hidden-consumer-overrides)
5.  [Architecture Risk Assessment](#architecture-risk-check)
6.  [Engineering Annotations](#engineers-notes)

## Overview
Standard Google Cloud quota lists often miss critical infrastructure metrics like network egress and model-specific rate limits. This protocol forces the CLI agent to probe non-standard API surfaces to reveal the "Effective Limits" applied to the EVO ULTRA organization.

## Phase 1: The "Ghost" Scan (Network & Egress)
Egress is a throughput limit, not a count limit. It lives in Compute Project Info rather than Service Usage.

### Extraction Commands
```bash
# Reveal Global Egress Caps
gcloud compute project-info describe --format="json(quotas, commonInstanceMetadata)" > project_network_limits.json

# Check Specific Regional Egress (e.g., us-central1)
gcloud compute regions describe us-central1 --format="json(quotas.name, quotas.limit, quotas.usage)" | grep "INTERNET_EGRESS_BANDWIDTH"

# Verify Tier 1 Networking Status
gcloud compute project-info describe --flatten="commonInstanceMetadata.items[]" --filter="key=default-network-tier"
```

## Phase 2: The "Brain" Scan (Vertex AI & Gemini)
Multi-model swarms require model-specific QPM (Queries Per Minute) mapping.

### Extraction Commands
```bash
# Force-list model-specific rate limits
gcloud services quota list --service=aiplatform.googleapis.com --consumer --format="table(metric, displayName, limit, unit)"

# Target Custom Model Serving
gcloud services quota list --service=aiplatform.googleapis.com --filter="metric:custom_model_serving"
```

## Phase 3: The "Mega" Scan (Hidden Consumer Overrides)
Revealing non-public limits applied by Enterprise credits ($1,000 promo).

### Extraction Commands
```bash
# The "Truth" Command (Alpha API)
gcloud alpha services quota list --consumer --format="json" > absolute_all_quotas.json

# Map Service Usage API limits
gcloud services quota list --service=serviceusage.googleapis.com
```

## Architecture Risk Check
-   **The Egress Trap:** Egress is often a billing gate, not a hard stop. High-frequency agent communication can exhaust credits in hours without hitting an API error.
-   **The API Handshake:** Agents cannot communicate if `servicenetworking.googleapis.com` is disabled. Ensure this is part of every genesis script.

## Engineering Notes
> **Engineer's Note (Egress):** If `INTERNET_EGRESS_BANDWIDTH` is < 100 in `project_network_limits.json`, the swarm will bottleneck during high-intensity scanning operations.
>
> **Engineer's Note (Billing):** The $1,000 Vertex credits are restricted to **Agent Builder SKUs** (`discoveryengine.googleapis.com`). Direct calls to Gemini (`aiplatform.googleapis.com`) burn the general $300 trial.

---
*Protocol Version: 2.1.0 (Production)*
