# Agent Health Monitor

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Digital Intensity Ltd operates Agent Health Monitor (AHM, agenthealthmonitor.xyz), trust and health verification for autonomous agents on Base L2. Fourteen pay-per-call REST endpoints score any agent wallet: quick and premium risk scores (Nansen labels), health and wash diagnostics, the 0-100 Agent Health Score with A-F grades, tiered trust routing (instant_settle / escrow / reject) for payment middleware, gas optimisation, ready-to-sign retry transactions, 30-day webhook alerts and an all-in-one protection run, priced $0.001 to $25.00 per call. Agents pay per call in USDC over x402 (HTTP 402 + PAYMENT-REQUIRED, discovery at /.well-known/x402); humans buy an X-API-Key credit pack via Stripe ($9 / $39 one-time, $99/month). Published as OpenAPI 3.1.0, open source (MIT) on GitHub, with the ahm-shield Python SDK. AHM Verify scores delivered agent output at $0.50 per verdict. AHM also serves an ERC-8004 registration file, a legacy-path A2A agent card and a public roadmap.

**Areas:** Agents · Agent Trust · Risk Scoring · Wallet Intelligence · Blockchain · Base · x402 · Agentic Commerce · Monitoring · Webhook · Web3 · Verifiable Credentials

## Agent Health Monitor on APIs.io

Everything profiled for Agent Health Monitor is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/agenthealthmonitor-xyz/](https://apis.io/providers/agenthealthmonitor-xyz/)** — or go straight to one of the APIs or properties below.

### APIs (14)

- [Agent Health Monitor Admin API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-admin-api/) — Internal admin endpoints protected by X-Internal-Key header. Security activity logs, trust registry, and registry scan triggers.
- [Agent Health Monitor Alerts API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-alerts-api/) — Subscribe wallets to automated health monitoring with webhook alerts. Health checks run every 6 hours; alerts fire when configurable thresholds are breached.
- [Agent Health Monitor Billing API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-billing-api/) — Stripe checkout webhooks and API key management for fiat-paid access.
- [Agent Health Monitor Coupon Access API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-coupon-access-api/) — Partner coupon routes — access any paid endpoint for free with a valid coupon code. Rate-limited to 5 requests per IP per minute.
- [Agent Health Monitor Discovery & Info API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-discovery-info-api/) — Service discovery, pricing info, ecosystem statistics, and x402/ERC-8004 well-known documents for automated agent registration.
- [Agent Health Monitor Health API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-health-api/) — The Health API from Agent Health Monitor — 1 operation(s) for health.
- [Agent Health Monitor Health & Hygiene API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-health-hygiene-api/) — Wallet health diagnosis, hygiene scans, composite Agent Health Score (AHS), and visual report cards. Core analysis endpoints from $0.50 to $2.00.
- [Agent Health Monitor Optimization API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-optimization-api/) — Gas optimization reports and failed-transaction retry bot. Returns per-transaction-type savings and ready-to-sign EIP-1559 retry payloads.
- [Agent Health Monitor Outputs API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-outputs-api/) — The Outputs API from Agent Health Monitor — 1 operation(s) for outputs.
- [Agent Health Monitor Protection API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-protection-api/) — Autonomous protection agent that triages risk and runs the appropriate combination of health, optimization, and retry services automatically.
- [Agent Health Monitor Scoring & Risk API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-scoring-risk-api/) — Risk scoring, counterparty analysis, and wallet network mapping. Fast pre-flight checks from $0.001 to deep Nansen-enriched analysis at $0.10.
- [Agent Health Monitor Specs API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-specs-api/) — The Specs API from Agent Health Monitor — 1 operation(s) for specs.
- [Agent Health Monitor Utility API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-utility-api/) — Health checks and AI chat assistant.
- [Agent Health Monitor Verdicts API](https://apis.io/apis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-verdicts-api/) — The Verdicts API from Agent Health Monitor — 1 operation(s) for verdicts.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Agenthealthmonitor Xyz Alerts Webhooks](https://apis.io/asyncapis/agenthealthmonitor-xyz/agenthealthmonitor-xyz-alerts-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [agenthealthmonitor-xyz](https://apis.io/servers/agenthealthmonitor-xyz/agenthealthmonitor-xyz/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Agenthealthmonitor Xyz Agentic Access](https://apis.io/agentic-access/agenthealthmonitor-xyz/agenthealthmonitor-xyz-agentic-access/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Agenthealthmonitor Xyz Openapi Overlay](https://apis.io/overlays/agenthealthmonitor-xyz/agenthealthmonitor-xyz-openapi-overlay/)
- [Agenthealthmonitor Xyz Verify Openapi Overlay](https://apis.io/overlays/agenthealthmonitor-xyz/agenthealthmonitor-xyz-verify-openapi-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Agenthealthmonitor Xyz Authentication](https://apis.io/security/agenthealthmonitor-xyz/agenthealthmonitor-xyz-authentication/)
- [Agenthealthmonitor Xyz Domain Security](https://apis.io/security/agenthealthmonitor-xyz/agenthealthmonitor-xyz-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Agenthealthmonitor Xyz Plans Pricing](https://apis.io/plans/agenthealthmonitor-xyz/agenthealthmonitor-xyz-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Agenthealthmonitor Xyz Rate Limits](https://apis.io/rate-limits/agenthealthmonitor-xyz/agenthealthmonitor-xyz-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://agenthealthmonitor.xyz/)
- [Documentation](https://docs.agenthealthmonitor.xyz/)
- [Getting started](https://docs.agenthealthmonitor.xyz/#getting-started)
- [API reference](https://agenthealthmonitor.xyz/docs)
- [Pricing](https://docs.agenthealthmonitor.xyz/#pricing)
- [Sign up](https://agenthealthmonitor.xyz/pay-by-card)
- [Support](https://docs.agenthealthmonitor.xyz/#design-partner)
- [Blog](https://blog.agenthealthmonitor.xyz/)
- [GitHub](https://github.com/moonshot-cyber)

## API Evangelist rating

**Kin Score 48.3** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 48.8 |
| Contract governance | 18.2 |
| Operational transparency | 18.4 |
| Developer ergonomics | 73.2 |
| Access clarity | 55.3 |

**Agent readiness 32.6** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | flavored (partial credit) |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | mostly |

**Regulatory alignment 15.2** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/agenthealthmonitor-xyz/](https://apis.io/providers/agenthealthmonitor-xyz/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Agent Health Monitor: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/agenthealthmonitor-xyz/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
