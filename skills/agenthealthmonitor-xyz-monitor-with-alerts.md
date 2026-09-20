---
name: Monitor a wallet with webhook alerts
description: Subscribe a wallet to 30 days of 6-hourly health checks, point the alerts at a Slack, Discord or generic JSON
  webhook with thresholds, check status, and unsubscribe.
api: openapi/agenthealthmonitor-xyz-openapi.yml
provider: agenthealthmonitor-xyz
base_url: https://agenthealthmonitor.xyz
operations:
- subscribe_alerts_alerts_subscribe__address__get
- configure_alerts_alerts_configure_post
- alert_status_alerts_status__address__get
- unsubscribe_alerts_alerts_unsubscribe__address__delete
generated: '2026-09-19'
method: generated
source: API Evangelist, from the provider OpenAPI 1.8.0 and docs; not provider-published
---

# Monitor a wallet with webhook alerts

Subscribe a wallet to 30 days of 6-hourly health checks, point the alerts at a Slack, Discord or generic JSON webhook with thresholds, check status, and unsubscribe.

## When to use
You operate (or depend on) an agent wallet and want to be told when its health score drops, its failure rate climbs or it starts wasting gas — without polling paid endpoints.

## Steps
1. **Subscribe (paid)** — `GET /alerts/subscribe/{address}` (`subscribe_alerts_alerts_subscribe__address__get`, $2.00 USDC or 1 credit). Activates 30 days of monitoring; calling it again on an active subscription **extends by 30 days and charges again**, so check status first.
2. **Configure (free)** — `POST /alerts/configure` (`configure_alerts_alerts_configure_post`) with `ConfigureRequest`: `address`, `webhook_url` (public https URL — private/loopback/.internal hosts are refused with 400), `webhook_type` = `generic` | `slack` | `discord`, and `thresholds` (`AlertThresholds`: `health_score` alert when below, `failure_rate` percent alert when above, `waste_usd` alert when above). Re-POST to change it.
3. **Check (free)** — `GET /alerts/status/{address}` (`alert_status_alerts_status__address__get`) returns the thresholds, `last_check_at`, `last_alert_at`, `alerts_sent`.
4. **Stop (free)** — `DELETE /alerts/unsubscribe/{address}` (`unsubscribe_alerts_alerts_unsubscribe__address__delete`). This is the only reversal operation in the API; no refund of the remaining period is stated.

## What arrives
Generic JSON: `{"address": "0x…", "timestamp": "2026-09-19T12:00:00Z", "alerts": [{"type": "...", "message": "..."}]}`. Slack gets `{"text": ...}`, Discord `{"content": ...}`. Deliveries are unsigned, single-attempt, 10 s timeout — verify by re-reading `/alerts/status/{address}` rather than trusting the POST alone.

## Rules
- Checks run every 6 hours; do not expect real-time alerts.
- 60/min per-IP limit on subscribe and configure.
- Pay with x402 or `X-API-Key`; configure/status/unsubscribe need neither but require an active subscription.
