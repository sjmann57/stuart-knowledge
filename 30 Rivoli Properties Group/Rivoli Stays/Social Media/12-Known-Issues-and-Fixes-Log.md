---
title: Rivoli Stays - Known Issues and Fixes Log
tags: [rivoli-stays, incidents, technical, log]
aliases: [Incident Log, Known Issues, Bug History]
---

# Rivoli Stays — Known Issues and Fixes Log

A chronological record of automation incidents affecting Rivoli Stays social/blog publishing, kept so the same mistakes aren't repeated. Cross-referenced with the technical articles.

## Data store list defaults to ~10 records

`data-store-records_list` on store `129528` returns only the first ~10 records when no `limit` is passed. This caused a weekly review (10 Jul 2026) to wrongly report several posts as never having existed, and caused duplicate-key errors when re-creating already-approved records.

**Fix:** Always call with `limit: 100` or higher before reviewing status, assigning new IDs, or creating records. See [[09-Automation-Architecture-Make]].

## Weekly plan drafted but never approved into the store (2 consecutive weeks lost)

Two consecutive weeks (w/c 17 Aug and w/c 24 Aug 2026) failed to publish anything because the weekly plan was drafted into a markdown file but never actually loaded/approved into the Make.com data store, so the daily monitor found nothing to publish.

**Fix (29 Aug 2026, standing policy):** Any generated post with a real image URL is now auto-approved and queued to the data store as `status: "approved"` in the same run. Only an image-less post stays `pending`, waiting for a human to add an image and approve via the dashboard. See [[13-Weekly-Content-Plan-Workflow]].

## Dashboard "Approve All" overwrote already-posted records

The Rivoli Social Dashboard's approve action used `data-store-records_replace` (a full overwrite) built from a stale in-memory snapshot. Clicking "Approve All" after the daily monitor had already published a post reset that post from `status: posted` back to `approved` and wiped `postedAt`. Concretely, on 19 Aug 2026 this reset post `w-046` (posted at 10:05) back to approved at 10:54.

**Fix (19 Aug 2026):** `approvePost()` now re-reads the live record via `data-store-records_list` immediately before writing. If the live status is already `posted`, it skips the write and just reflects "posted" in the UI; otherwise it preserves the existing `postedAt`. See [[14-Rivoli-Social-Dashboard-Reference]].

## "Accepted" webhook response treated as proof of publishing

A webhook returning "Accepted" only means the payload was received/queued — not that it published. If the target Make scenario is inactive, or the post errors, "Accepted" is still returned and nothing goes live.

- **14 Aug 2026:** Both social scenarios auto-disabled after errors (LinkedIn: 4000-character overflow; Meta: an Instagram "only photo or video accepted" error). The post monitor kept marking records "posted" based on "Accepted" alone, so `w-044`-`w-048` showed "posted" while nothing had actually published for over a week. Corrected to "missed" on 22 Aug.
- **Recurred 3 Sep 2026:** despite a memory of the rule existing, the actual scheduled task prompt had never been updated to include the verify step. Scenario `5857917` had been sitting inactive since 14 Aug the entire time; `w-053` and `w-054` were marked "posted" on "Accepted" alone while nothing published to Facebook/Instagram for three weeks. Stuart caught it by checking Facebook directly.

**Fix:** After any webhook POST, wait ~15 seconds and check `executions_list` for that scenario. Confirm the newest execution status is **1 (success)** before marking a record "posted"; status **3** = error, leave it "missed"/"approved" and report the failure. Critically: **a memory recording a rule is not enough** — the live scheduled-task prompt itself must implement the check. See [[09-Automation-Architecture-Make]] and [[10-LinkedIn-Publishing-Rules]].

## LinkedIn weekly article routinely exceeded the character limit

The scheduled task originally asked for a 600-900 word LinkedIn "article", which is roughly 4000-5500 characters and always exceeded LinkedIn's 4000-character `ShareCommentary` limit, causing repeated publish failures.

**Fix:** Cap the weekly LinkedIn output at ~550-600 words / under 3900 characters, verify the character count before sending. See [[10-LinkedIn-Publishing-Rules]].

## Repeated character-limit failures auto-disabled the LinkedIn scenario

Make's error threshold (`maxErrors: 3`) auto-disables a scenario after repeated failures. Once disabled, the webhook still returns "Accepted" but only queues — nothing publishes. This combined with the character-limit bug to cause silent multi-week outages.

**Fix:** Keep posts under the character ceiling to prevent the auto-disable trigger in the first place; if it happens anyway, reactivating the scenario drains a *correctly-sized* queue, but oversized items will simply fail and re-disable it (see next item).

## Stuck oversized items block queue drainage entirely

Once oversized items are queued, reactivating the scenario does **not** clear them — Make immediately reprocesses all queued items, they fail again on the same error, and the scenario auto-disables itself again within seconds. There is no API/MCP tool to clear a webhook queue.

**Fix:** Must be cleared manually in the Make.com UI (Webhooks → the webhook → Queue tab → select-all → Delete) by Stuart or Jeanie directly — Claude cannot log in on their behalf.

## Blog scenario's own internal schedule caused duplicate posts

Scenario `5868161` has an internal 15-minute polling trigger. Left active after a manual run, it re-fired the same hardcoded blueprint repeatedly, creating duplicate WordPress articles.

**Fix:** A lock file keyed by ISO week, plus deactivating the scenario again immediately after a successful publish. See [[11-WordPress-Blog-Publishing]].

## General Lesson

Across nearly every incident above, the root cause was the same shape: an automation step that looked successful (a webhook "Accepted", a memory note describing a fix) wasn't actually verified against live state (execution status, the live scheduled-task prompt, the live data-store record). **Always verify against the current live system, not the last known-good description of it.**

## Related

- [[09-Automation-Architecture-Make]]
- [[10-LinkedIn-Publishing-Rules]]
- [[11-WordPress-Blog-Publishing]]
- [[13-Weekly-Content-Plan-Workflow]]
- [[14-Rivoli-Social-Dashboard-Reference]]
