---
title: Rollout Status
tags: [rpm, rollout, status]
updated: 2026-09-15
---

# Rollout Status

**Overall status as of 15 September 2026: live and operating.** Posting scenario (7257618) works across all three platforms including LinkedIn. Per-platform targeting is confirmed intentional (informational field, not a filter), not an open defect. Weekly content-draft task is live and queuing real posts with sourced claims and Unsplash images. Dashboard is live as a published Claude Artifact. Daily publishing itself is still a manual recipe, not yet an unattended scheduled task. Case Study Library remains empty — still the standing Phase 0 blocker.

## Phase 0 — Foundations

| Item | Status |
|---|---|
| Confirm/create Facebook and Instagram pages | **Done** — both exist and are connectable |
| Confirm/create LinkedIn Company Page, register developer app, secure Community Management API access | **Done** — access requested and granted 4 September 2026 |
| Create the new Make.com data store | **Done differently** — no new store created; existing shared store (129528) extended instead |
| Gather first 3–5 real, consented landlord testimonials | **Not done — still zero as of 13 September 2026.** Unchanged since 4 September. The single biggest open Phase 0 item; the Social Proof pillar cannot produce content until the library has entries |
| Confirm UTM parameters | **Done, 5 September 2026** — convention set (see [[10 - KPIs]]), but not yet confirmed wired into live generation logic |

## Phase 1 — Build

| Item | Status |
|---|---|
| Build the Make.com posting scenario (Meta + LinkedIn branches) | **Done** — scenario 7257618, live across all three platforms |
| Build the dashboard artifact | **Done, but shipped as a published Claude Artifact instead of a Cowork-desktop file** — see [[08 - Dashboard (Command Centre)]] |
| Build the two scheduled tasks (weekly content plan, daily post monitor) | **Half done** — weekly content-draft task is live; daily post monitor is still a manual recipe, not a scheduled task — see [[14 - Operational History Log]] §14.5 |

## Phase 2 — Soft launch

Run at reduced cadence (one post a week) for 2–3 weeks to validate the LinkedIn publishing flow end-to-end before trusting it to auto-fire daily. **Not formally tracked as started or complete** — three posts have gone live (`rm-001` through `rm-003`) and six more are queued, which is broadly consistent with a soft-launch cadence, but no explicit phase-gate decision has been recorded.

## Phase 3 — Full cadence

Move to the full posting cadence ([[04 - Content Strategy]]) once Phase 2 has produced at least one successful LinkedIn post with no manual intervention. **Not yet reached** — publishing still requires the manual scenario-toggle recipe.

## Related

[[02 - Corporate Structure and Two-Option Offering]] · [[14 - Operational History Log]] · [[16 - Case Study Library]] · [[12 - Open Questions and Decisions]]
