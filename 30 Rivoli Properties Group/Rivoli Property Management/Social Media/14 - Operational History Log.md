---
title: Operational History Log (6–13 September 2026)
tags: [rpm, history, log]
updated: 2026-09-15
---

# Operational History Log — What Actually Happened, 6–13 September 2026

This period covers real decisions and infrastructure changes made in Cowork sessions and conversations that were not reflected in the technical spec document until it was brought up to date to v2.0 on 13 September 2026. Section numbers below match the spec's own §14 for cross-reference.

## §14.0 — Corporate and product shape changed

RPM is being reformed as its own Ltd company under Rivoli Properties Ltd, now offering landlords two options rather than one. A dedicated "rivoli-property-management" skill was built (10 September 2026). Full detail: [[02 - Corporate Structure and Two-Option Offering]].

## §14.1 — Weekly content-draft task went live

The "Rivoli Management weekly content draft" scheduled task runs Mondays: researches dated sources, drafts posts rotated across both options and at least three pillars, sources Unsplash images, fact-checks claims, writes to the shared store. As of 13 September 2026 the store held three published posts (`rm-001`–`rm-003`, the ones originally test-posted on 5 September, now genuinely live) plus six further posts already drafted and approved for 15–25 September. Full detail: [[04 - Content Strategy]], [[15 - Post Log (Live and Queued)]].

## §14.2 — Approval governance changed

The original pillar-based whitelist was replaced by the fact-check-driven rule before go-live. Full detail: [[07 - Approval Governance]].

## §14.3 — Dashboard shipped as a published Artifact, not a desktop file

The dashboard was built, then rebuilt to fix real problems in the first version. Full detail: [[08 - Dashboard (Command Centre)]].

## §14.4 — Per-platform targeting confirmed intentional

Stuart reviewed the actual behaviour on 10 September 2026 and confirmed it is not a bug: scenario 7257618 posts every approved record to Facebook, Instagram and LinkedIn regardless of that record's `platforms` field. His words: *"I see the two posts on all platforms, which is what I expected."* The `platforms` field stays in the schema and dashboard as the intended audience for editorial purposes only. Treat this as closed.

`posted_urls` capture (the other item left open after the 5 September test) is still not solved — see [[13 - Reliability Incidents]].

## §14.5 — How publishing actually happens today

No unattended daily post monitor has been built yet. In its place, publishing an approved record is a **manual recipe**, run by Stuart or a Claude session on his behalf:

1. Deactivate scenario 5969045 (Rivoli Stays' LinkedIn scenario) to free a slot under the Free plan's 2-active-scenario cap.
2. Activate scenario 7257618 (Rivoli Management — Publish to Social Media).
3. POST the record's `caption` and `image_url` directly to the webhook: `https://hook.eu1.make.com/5xkwoebixcijmudlbjbb80hua4tski8t`.
4. Confirm via `executions_list` that the newest execution shows **`operations: 4`** — not just an HTTP 200/"Accepted" response and not just `status: 1` (both of which a false-success run can also show; a genuine no-op shows `operations: 1`).
5. Deactivate 7257618, then reactivate 5969045.

This recipe published `rm-001` and `rm-002` successfully on **10 September 2026**, after the networking fix below unblocked it. Building this into a real unattended scheduled task — including safe recovery from a toggle that fails partway — is the main piece of original Phase 1 still outstanding.

## §14.6 — Two operational fixes worth recording

- **Image sourcing policy.** RPM content is about other people's properties, not Rivoli's own portfolio, so it must never reuse Rivoli Stays' real property photography. Every image is sourced from Unsplash instead. Full detail: [[17 - Image Sourcing Policy]].
- **Network egress allowlist.** Reaching LinkedIn and firing the Make webhook directly from a Claude session required adding `linkedin.com`, `instagram.com`, and `hook.eu1.make.com` to the account's Capabilities → domain allowlist — distinct from, and in addition to, the per-action approval step that separately gates sensitive actions (activating a live scenario, POSTing to an external webhook). Without this fix, the manual recipe above cannot be run from a Claude session at all, only from Stuart's own tools (e.g. Postman).

## Related

[[13 - Reliability Incidents]] · [[11 - Rollout Status]] · [[05 - Technical Architecture]]
