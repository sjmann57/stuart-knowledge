---
title: Rivoli Stays - Automation Architecture (Make.com)
tags: [rivoli-stays, automation, make.com, technical]
aliases: [Make.com Architecture, Automation Stack]
---

# Rivoli Stays — Automation Architecture (Make.com)

## Overview

Rivoli Stays' social posting is automated through Make.com scenarios, a Make.com data store acting as the queue/source of truth, and a Cowork artifact (the Rivoli Social Dashboard) that reads and writes to that same data store. A daily scheduled task ("Rivoli Post Monitor") publishes whatever is due.

## Make.com Account Constraint — 2 Active Scenarios Max

The Make.com plan in use caps **active scenarios at 2 simultaneously**. This is the single most important operational constraint in the whole system and has caused most of the historical outages (see [[12-Known-Issues-and-Fixes-Log]]).

Normally the two active slots are held by:

1. **Rivoli Stays — Publish to Social Media** (scenario ID `5857917`) — posts Facebook/Instagram content daily, always on.
2. **Rivoli Stays - Integration LinkedIn** (scenario ID `5969045`) — posts to the LinkedIn company page.

Any third scenario (WordPress blog publisher `5868161`, or an MS Security pipeline `5994792`) needs one of the above deactivated first, then reactivated afterward. Always re-check `scenarios_list` afterward to confirm the two social scenarios are back to `isActive: true`.

## The Data Store (ID 129528)

This is the **single source of truth** for what has been posted, is approved, or is pending. Both the daily Rivoli Post Monitor task and the Rivoli Social Dashboard artifact read/write to it.

**Critical technical gotcha:** `data-store-records_list` defaults to returning only ~10 records. **Always pass `limit: 100` or higher** — otherwise recent posts appear to be missing, IDs collide, or the weekly review wrongly reports posts as never-existing. See [[12-Known-Issues-and-Fixes-Log]].

### Record schema (per post)

```json
{
  "id": "w-0NN",
  "day": "Tuesday",
  "date": "15 September 2026",
  "isoDate": "2026-09-15",
  "time": "10:00",
  "timeLabel": "10:00am",
  "property": "Rivoli Mews",
  "type": "Property Showcase",
  "caption": "...",
  "image_url": "https://rivolistays.co.uk/wp-content/uploads/...",
  "status": "approved",
  "approvedAt": "ISO timestamp",
  "postedAt": "ISO timestamp or empty string"
}
```

Post IDs follow the sequence `w-010`, `w-011`, ... `w-0NN`, continuing from the highest existing key. Always check the full list of existing keys before assigning a new one — a "Duplicate key" error on create means the post is already queued (e.g. approved manually via the dashboard); report it as already handled rather than retrying with a different ID or overwriting.

The separate **Rivoli Property Management (RM)** brand uses a different key prefix (`rm-001`, `rm-002`, ...) in the *same* data store, filtered by a `brand: "RM"` field. See [[16-Rivoli-Property-Management-RM-Brand]].

## Post Status Lifecycle

`pending` (drafted, no image or awaiting human approval) → `approved` (queued, will fire on its scheduled day) → `posted` (published, `postedAt` set) — or `missed` (was due, never successfully published).

## Webhook URLs

See [[10-LinkedIn-Publishing-Rules]] for LinkedIn specifics and [[11-WordPress-Blog-Publishing]] for the blog scenario. The Facebook/Instagram posting webhook:

- **URL:** `https://hook.eu1.make.com/nl4uh706xiykzpd04ow9gu90r7rj4dx7`
- **Scenario:** Rivoli Stays — Publish to Social Media (`5857917`)
- **Payload fields:** `caption`, `image_url`, `page_id`

## Verification Rule (critical)

A webhook returning **"Accepted" only means the payload was received/queued — not that it published.** If the target scenario is inactive, or the post errors, "Accepted" is still returned and nothing goes live. Always wait ~15 seconds after posting, then check `executions_list` for that scenario and confirm the newest execution status is **1 (success)** before marking a data-store record "posted". Status **3** means error — leave the record `approved`/`missed` and report the failure. Full incident history in [[12-Known-Issues-and-Fixes-Log]].

## Related

- [[10-LinkedIn-Publishing-Rules]]
- [[11-WordPress-Blog-Publishing]]
- [[12-Known-Issues-and-Fixes-Log]]
- [[14-Rivoli-Social-Dashboard-Reference]]
