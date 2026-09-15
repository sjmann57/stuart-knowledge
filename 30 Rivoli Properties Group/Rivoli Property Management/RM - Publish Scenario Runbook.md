---
title: RM - Publish Scenario Runbook
tags: [rivoli-management, tools, runbook]
---

# Publish Scenario Runbook

Rivoli's Make.com plan caps **active scenarios at 2**. Those slots are normally held by:
- `5857917` — "Rivoli Stays — Publish to Social Media" (always on, posts RS content daily)
- `5969045` — "Rivoli Stays - Integration LinkedIn"

`7257618` — "Rivoli Management — Publish to Social Media" (webhook-triggered, posts to Facebook/Instagram/LinkedIn) can't just be left active alongside those two — activating it requires first deactivating one of the other scenarios (`5969045` is the lower-risk swap, since it's not RS's daily driver).

## Manual publish recipe
1. Deactivate `5969045`
2. Activate `7257618`
3. POST the record's caption + image_url directly to `https://hook.eu1.make.com/5xkwoebixcijmudlbjbb80hua4tski8t`
4. Confirm via `mcp__Make__executions_list` that the newest execution shows `operations:4` — **not** just `status:1`, and not the webhook's "Accepted" response; both are insufficient proof alone. A false-success run shows `operations:1`.
5. Deactivate `7257618`
6. Reactivate `5969045`

This is expected/confirmed behaviour, not a workaround for a bug — Stuart: *"you will need to activate the scenario each time."*

Note: `7257618` always posts to Facebook, Instagram, **and** LinkedIn on every run regardless of a record's `platforms` field — that field is informational only and doesn't filter which channels a post goes to.

## Related
- [[Rivoli Property Management (MOC)]]
- [[RM - Social Content Pipeline]]
- [[RM - Tools & Integrations]]
