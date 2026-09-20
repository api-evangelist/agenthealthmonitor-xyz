---
name: Score an agent wallet (AHS, grade, report card, batch)
description: Produce the 0-100 Agent Health Score with A-F grade and dimension breakdown for one wallet, a shareable report
  card, or a batch of wallets.
api: openapi/agenthealthmonitor-xyz-openapi.yml
provider: agenthealthmonitor-xyz
base_url: https://agenthealthmonitor.xyz
operations:
- get_ahs_report_ahs__address__get
- get_ahs_batch_ahs_batch_post
- get_report_card_report_card__address__get
- get_agent_public_api_agent__address__get
- ecosystem_stats_api_ecosystem_stats_get
generated: '2026-09-19'
method: generated
source: API Evangelist, from the provider OpenAPI 1.8.0 and docs; not provider-published
---

# Score an agent wallet (AHS, grade, report card, batch)

Produce the 0-100 Agent Health Score with A-F grade and dimension breakdown for one wallet, a shareable report card, or a batch of wallets.

## When to use
You need the definitive composite health number for an agent wallet on Base — for a due-diligence report, a marketplace listing, a fleet review — rather than a quick go/no-go.

## Steps
1. **Free look-up first** — `GET /api/agent/{address}` (`get_agent_public_api_agent__address__get`, free) returns the wallet's `latest_ahs`, `latest_grade`, `percentile_rank`, `scan_count` and `last_scanned_at` from the nightly trust registry (47,766 wallets across ERC-8004, Arc, ACP, Celo, Olas as of 2026-09-20). If it is fresh enough, stop here.
2. **Fresh composite** — `GET /ahs/{address}` (`get_ahs_report_ahs__address__get`, $1.00). Returns `agent_health_score` 0-100, `grade` (A 90-100, B 75-89, C 60-74, D 40-59, E 20-39, F 0-19), `confidence`, `mode` (2D or 3D), `dimensions[]` with `wallet_hygiene` (weight 0.30) and `behavioural_patterns` (0.70) — or 0.25/0.45/0.30 with `infrastructure_health` when you supply an agent URL — plus `patterns_detected[]` (e.g. Zombie Agent, Stale Strategy) and `recommendations[]`.
3. **Batch** — `POST /ahs/batch` (`get_ahs_batch_ahs_batch_post`, body `AHSBatchRequest {addresses[]}`): up to 10 wallets per x402 call ($10.00) or up to 25 per API-key call (1 credit per wallet).
4. **Shareable artefact** — `GET /report-card/{address}` (`get_report_card_report_card__address__get`, $2.00) returns a 1200x675 PNG with percentile ranking against every scanned wallet and a share URL.
5. **Context** — `GET /api/ecosystem-stats` (`ecosystem_stats_api_ecosystem_stats_get`, free) gives the ecosystem average AHS and grade distribution to benchmark against.

## Rules
- Grades are the provider's only grade table; do not invent thresholds. `INSUFFICIENT` confidence is *unrated*.
- `/ahs/batch` over x402 rejects more than 10 addresses (422); over an API key more than 25.
- Per-IP limits: 60/min on `/ahs` and `/ahs/batch`, 20/min on `/report-card`.
- Pay with x402 (402 + `PAYMENT-REQUIRED` -> `X-PAYMENT`) or `X-API-Key`. Every call is billed; there is no dry-run for scoring.
