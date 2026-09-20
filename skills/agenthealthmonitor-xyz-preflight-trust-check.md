---
name: Pre-flight trust check and payment routing
description: Before paying or delegating to another agent wallet on Base, get a risk score and a one-word routing decision
  (instant_settle / escrow / reject), optionally under your own routing policy.
api: openapi/agenthealthmonitor-xyz-openapi.yml
provider: agenthealthmonitor-xyz
base_url: https://agenthealthmonitor.xyz
operations:
- get_risk_score_risk__address__get
- get_trust_route_ahs_route__address__get
- get_routing_policy_ahs_route_policy_get
- put_routing_policy_ahs_route_policy_put
- get_premium_risk_score_risk_premium__address__get
generated: '2026-09-19'
method: generated
source: API Evangelist, from the provider OpenAPI 1.8.0 and docs; not provider-published
---

# Pre-flight trust check and payment routing

Before paying or delegating to another agent wallet on Base, get a risk score and a one-word routing decision (instant_settle / escrow / reject), optionally under your own routing policy.

## When to use
You are about to route a payment, accept a job, or enter a contract with another autonomous agent identified by an Ethereum wallet address on Base (eip155:8453) and need an evidence-based go / hold / stop signal in one call.

## Steps
1. **Cheapest screen** — `GET /risk/{address}` (`get_risk_score_risk__address__get`, $0.001 USDC). Returns `risk_score` 0-100, `risk_level` LOW|MEDIUM|HIGH|CRITICAL and a one-line `verdict`. LOW (0-30) is safe to transact; HIGH (61-100) means do not transact.
2. **Routing decision** — `GET /ahs/route/{address}` (`get_trust_route_ahs_route__address__get`, $0.01). Returns `routing_recommendation` = `instant_settle` (AHS grade A/B), `escrow` (grade C) or `reject` (D/E/F), plus `agent_health_score`, `grade`, `confidence`, `scored_at`, `stale`. Enforce it programmatically: settle, hold funds until delivery, or refuse.
3. **Own policy (optional)** — read the defaults with `GET /ahs/route/policy` (`get_routing_policy_ahs_route_policy_get`) and replace them with `PUT /ahs/route/policy` (`put_routing_policy_ahs_route_policy_put`, $0.01, body `RoutingPolicyRequest`). Rules the server enforces (422 otherwise): every grade A-F assigned to exactly one of instant/escrow/reject; no escrow grades when `escrow_disabled`; allowlist max 1000 valid addresses, none of them your own, all of them Grade C or above.
4. **Deeper profile when the stakes are high** — `GET /risk/premium/{address}` (`get_premium_risk_score_risk_premium__address__get`, $0.05) adds Nansen smart-money labels, PnL summary and operational health (1h/24h revert rates, nonce gaps).

## Paying
- No account: call the endpoint, receive `402` with a base64 `PAYMENT-REQUIRED` header, sign the EIP-3009 USDC authorization for one `accepts[]` entry (network `eip155:8453`, `maxTimeoutSeconds` 300) and resend with `X-PAYMENT`. An x402 client library does this for you.
- Or send `X-API-Key: ahm_live_...` (Stripe credit pack: 1 call = 1 credit).
- The Python SDK `ahm-shield` wraps step 2: `AHMShield(api_key).route(address)` and a `@shield.guard(min_grade="C")` decorator.

## Rules
- Treat `confidence: INSUFFICIENT` (thin history) as *unrated*, not as *bad* — the provider says so explicitly.
- `stale: true` means the score is from an old nightly scan; pay for a fresh `/ahs` if the decision is expensive.
- Every x402 call is a separate payment; a retried call is charged again. There is no Idempotency-Key.
- Per-IP limits: 60/min on `/risk`, 20/min on `/ahs/route/{address}`; 429 carries no Retry-After — wait out the minute.
- Errors are `{"detail": ...}`; 422 = malformed address (must be 0x + 40 hex) or a policy that breaks the invariants above.
