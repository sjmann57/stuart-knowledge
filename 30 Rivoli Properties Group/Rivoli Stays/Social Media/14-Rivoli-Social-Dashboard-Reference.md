---
title: Rivoli Stays - Social Dashboard Reference
tags: [rivoli-stays, dashboard, artifact, technical]
aliases: [Social Dashboard, rivoli-social-dashboard]
---

# Rivoli Stays — Social Dashboard Reference

## What It Is

A Cowork Artifact (self-contained HTML, artifact ID `rivoli-social-dashboard`) that acts as the social media command centre. It is **live-synced** to the Make.com data store (`129528`) on every load via `initFromDataStore()`, so approval/posted status always reflects reality without needing a manual rewrite for status changes.

## Tabs

- **Dashboard** — follower counts (Facebook/Instagram), summary stats, recent published posts.
- **This Week** — the current `WEEKLY_PLAN` array as editable cards (image URL, caption, approve/schedule button), synced live from the data store.
- **Post History** — all posts in the `POSTS` array, filterable by platform.
- **New Post** — an ad hoc drafting form (optimal posting time banner, caption/image/property/type fields, publish or save as draft).
- **Events Calendar** — the `EVENTS` array, a running reference of local events and audiences (see [[08-Local-Events-Reference]] for the underlying content).
- **Strategy Insights** — best content type/property by engagement, posting-time recommendations, an engagement-over-time chart (Chart.js), and free-text "strategy points" including a running incident log summary.

## Data Structures in the Artifact

- **`POSTS`** — historical post log with engagement figures (likes/comments/reach). Only updated with *real* figures once a human supplies them; never fabricated.
- **`WEEKLY_PLAN`** — the current week's 3-4 posts, replaced each Friday by the weekly workflow. Each entry: `id`, `day`, `date`, `isoDate`, `time`, `timeLabel`, `platforms`, `property`, `type`, `imageUrl`, `imageNote`, `caption`, `status`, `savedToStore`.
- **`EVENTS`** — the reference events list shown in the Events Calendar tab.

## Approve Flow (`approvePost()`)

Because `data-store-records_replace` is a full overwrite (not a merge), the approve function **re-reads the live data-store record immediately before writing**. If the live status is already `posted`, it skips the write and just reflects "posted" in the UI rather than resetting it back to "approved" (this guard was added after a real incident — see [[12-Known-Issues-and-Fixes-Log]]).

## Known Cosmetic Issues (benign, don't block functionality)

- External `rivolistays.co.uk` preview images are blocked by the artifact's CSP (`img-src 'self' data:'`), so property photos may not render inside the dashboard's own preview even though the URLs are valid for the actual social post.
- A benign `TypeError: Cannot set properties of undefined (setting 'display')` sometimes fires during render — does not block approving or posting.

## Editing Rules When Updating the Dashboard

When the weekly workflow (see [[13-Weekly-Content-Plan-Workflow]]) updates this artifact:

- Only touch the `WEEKLY_PLAN` array, the `week-title` text, and the two hardcoded fallback banner strings.
- Leave `POSTS`, `EVENTS`, and all rendering functions untouched unless real engagement/follower data needs folding in.
- The artifact file itself is read-only once published — edits must be written to a fresh file in the working directory and pushed via `update_artifact`, not edited in place at its live path.

## Related

- [[09-Automation-Architecture-Make]]
- [[12-Known-Issues-and-Fixes-Log]]
- [[13-Weekly-Content-Plan-Workflow]]
