---
name: Diagnose, clean and optimise an agent wallet
description: Run the diagnostic ladder on your own agent wallet — health report, wash (hygiene) scan, gas optimisation, retry
  of failed transactions, or the all-in-one protection run — using the free previews before the expensive calls.
api: openapi/agenthealthmonitor-xyz-openapi.yml
provider: agenthealthmonitor-xyz
base_url: https://agenthealthmonitor.xyz
operations:
- get_health_report_health__address__get
- get_wash_report_wash__address__post
- get_optimization_report_optimize__address__get
- retry_preview_retry_preview__address__get
- get_retry_transactions_retry__address__get
- protection_preview_agent_protect_preview__address__get
- get_protection_report_agent_protect__address__get
- get_counterparties_counterparties__address__get
- get_network_map_network_map__address__get
generated: '2026-09-19'
method: generated
source: API Evangelist, from the provider OpenAPI 1.8.0 and docs; not provider-published
---

# Diagnose, clean and optimise an agent wallet

Run the diagnostic ladder on your own agent wallet — health report, wash (hygiene) scan, gas optimisation, retry of failed transactions, or the all-in-one protection run — using the free previews before the expensive calls.

## When to use
Your agent's wallet on Base is failing transactions, overpaying gas, accumulating dust/spam tokens, or you simply want a maintenance report with concrete fixes.

## Steps
1. **Preview before paying** — `GET /agent/protect/preview/{address}` (`protection_preview_agent_protect_preview__address__get`, free) returns the risk level and the list of services the $25 protection run *would* execute; `GET /retry/preview/{address}` (`retry_preview_retry_preview__address__get`, free) returns `retryable_count`, `total_estimated_retry_cost_usd` and `potential_value_recovered_usd`. If both say there is nothing to fix, stop.
2. **Health report** — `GET /health/{address}` (`get_health_report_health__address__get`, $0.50): `health_score`, `success_rate_pct`, `wasted_gas_eth`, `estimated_monthly_waste_usd`, `out_of_gas_count`, `reverted_count`, `nonce_gap_count`, `top_failure_type`, `recommendations[]` with severity.
3. **Wash scan** — `POST /wash/{address}` (`get_wash_report_wash__address__post`, $0.50): dust accumulation, spam exposure, failed-tx patterns, gas efficiency, a composite cleanliness score and cleanup recommendations (`WashReport`, `WashIssue[]`).
4. **Optimise** — `GET /optimize/{address}` (`get_optimization_report_optimize__address__get`, $5.00): per-transaction-type gas plan (`GasOptimizationReport`, `TransactionTypeOptimization[]`).
5. **Retry failures** — `GET /retry/{address}` (`get_retry_transactions_retry__address__get`, $10.00): `RetryTransactionItem[]` ready-to-sign replacement transactions for recent failures. **Nothing is broadcast** — you sign and send them yourself, so review each one.
6. **Everything at once** — `GET /agent/protect/{address}` (`get_protection_report_agent_protect__address__get`, $25.00) triages risk and runs the appropriate services in one call (`ProtectionReport`, `ProtectionActionItem[]`).
7. **Who you deal with** — `GET /counterparties/{address}` ($0.10) and `GET /network-map/{address}` ($0.10) add Nansen-labelled counterparties and funder/deployer/multisig links.

## Rules
- Use the two free previews as the dry-run: there is no dry_run flag on the paid calls.
- Per-IP limits: 10/min on `/optimize` and `/retry/preview`, 60/min on the rest.
- Retry transactions are suggestions built from on-chain history; the API never holds keys or signs.
- Pay with x402 (402 + `PAYMENT-REQUIRED` -> `X-PAYMENT`, USDC on eip155:8453) or `X-API-Key`.
