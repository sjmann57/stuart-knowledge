---
title: RM - Tools & Integrations
tags: [rivoli-management, tools]
---

# Tools & Integrations

## Make.com scenarios
| ID | Name | Role |
|---|---|---|
| `5857917` | Rivoli Stays — Publish to Social Media | Always-on, posts RS content daily |
| `5969045` | Rivoli Stays - Integration LinkedIn | Swapped off temporarily to free a slot for RM publishing |
| `7257618` | Rivoli Management — Publish to Social Media | Webhook-triggered; posts RM content to FB/IG/LinkedIn |

See [[RM - Publish Scenario Runbook]] for the activation sequence — Rivoli's Make.com plan caps active scenarios at 2.

## Data store
Make.com data store `129528`, filtered to `brand=RM` — holds RM social post records (caption, image_url, option, platforms, etc.).

## Egress / allowlist notes
Domains that needed adding to the Capabilities → domain allowlist before Claude could reach them directly from a session: `linkedin.com`, `instagram.com`, `hook.eu1.make.com`. Distinct from, and in addition to, the per-action permission classifier that separately gates sensitive actions (activating a live-posting scenario, POSTing to an external webhook).

## Related
- [[Rivoli Property Management (MOC)]]
- [[RM - Publish Scenario Runbook]]
- [[RM - Command Centre Dashboard]]
- [[RM - Shared Systems with Rivoli Stays]]
