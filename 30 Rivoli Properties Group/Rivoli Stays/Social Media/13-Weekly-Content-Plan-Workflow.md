---
title: Rivoli Stays - Weekly Content Plan Workflow
tags: [rivoli-stays, workflow, scheduled-task, process]
aliases: [Weekly Workflow, Content Plan Process, rivoli-weekly-content-plan]
---

# Rivoli Stays — Weekly Content Plan Workflow

This is the standing process run by the `rivoli-weekly-content-plan` scheduled task, every Friday, acting as the social media strategist and SEO content manager for Rivoli Stays.

## Part 1 — Engagement Review

1. Work out the Monday of the week that just ended.
2. Read the Make.com data store (`129528`, `limit: 100`) and list posts with `status: "posted"` from that week (day, property, type).
3. If no records show `status: "posted"` for that week, say so plainly rather than presenting placeholder figures — never assume posts went live.
4. Flag any record for that week stuck as `approved` with no `postedAt` (due/overdue but never published), or `status: "missed"` — these indicate the Rivoli Post Monitor did not process every due post.
5. Present an engagement table (Likes / Comments / Reach per post) for the human to fill in — only for posts that actually show as posted.
6. Present a social metrics table (Facebook and Instagram: followers, best post reach last 7 days, impressions last 28 days) for the human to fill in.
7. Close with: "Reply with the figures and your approvals and I will update the dashboard."

## Part 2 — Next Week's Plan

### Step 1 — Research

Web search for: events in/near Derby and Burton upon Trent in the next 2-4 weeks; active construction/infrastructure projects (Balfour Beatty, Kier, Morgan Sindall, Skanska, Tarmac, Galliford Try, BAM, VINCI, local councils); business news (relocations, expansions); season and upcoming bank/school holidays. **Never invent an event or statistic — only use what a search result states.**

### Step 2 — Draft the Social Post Plan

3-4 posts for Tuesday 10:00, Wednesday 10:00, Thursday 9:00, and optionally Friday 10:00 (only with a strong event reason). Weekly mix: 1 property showcase, 1 B2B/contractor, 1 local/events, 1 social proof/direct booking push. See [[06-Social-Media-Content-Strategy]].

### Step 3 — Images

Never invent a URL. Check the Rivoli Social Dashboard's `POSTS`/`WEEKLY_PLAN` arrays and the data store first for a confirmed-real URL matching the property before fetching the live property page. If fetching fresh, use the `og:image` or a gallery image ending `-scaled.jpg` under `rivolistays.co.uk/wp-content/uploads/`. Must be `.jpg`. If no real image exists for a property, say so explicitly and leave `imageUrl` empty — that post stays PENDING, not auto-approved.

### Step 4 — SEO Article Suggestion

One suggestion from the four pillars in [[15-SEO-Article-Pillars]]: title, target keyphrase, word count, 5-6 bullet outline. Presented in chat only — does not go into either dashboard.

### Step 5 — Assign Post IDs

Sequential `w-0NN`, continuing from the highest existing key found in the data store. Check the full key list first (with `limit: 100`) to avoid collisions. A "Duplicate key" error on create means the post is already handled — treat as confirmation, don't retry with a different ID.

### Step 6 — Push the Plan to the Dashboard

1. `list_artifacts` to confirm the current path for artifact ID `rivoli-social-dashboard`.
2. Read that path to get the current HTML.
3. Replace the `WEEKLY_PLAN` array with the new week's posts, matching the existing schema. Set `status: 'approved'` and `savedToStore: true` for any post with a real image (per the auto-approve policy); `status: 'pending'` for an image-less post. Update the `week-title` text and the two hardcoded fallback banner strings (in the `catch` block of `initFromDataStore` and the `else` branch at the bottom of the script). Leave `POSTS`, `EVENTS`, and all rendering functions untouched unless real engagement/follower figures from Part 1 need folding in.
4. Write the updated HTML to a workspace file and call `update_artifact` for `rivoli-social-dashboard`.

### Step 7 — Auto-Approve and Queue (standing policy, set 29 Aug 2026)

For each post with a real image URL, queue it to the data store immediately:

1. Check the data store first — if the ID already exists with `status: "approved"`, it's already queued (e.g. a human approved it manually); skip it.
2. Otherwise `data-store-records_create` with the record schema from [[09-Automation-Architecture-Make]], `status: "approved"`, `approvedAt` set to now, `postedAt: ""`.
3. Never queue an image-less post — it stays `pending` for a human to add an image and approve via the dashboard.
4. Never post immediately and never create per-post scheduled tasks — the existing daily Rivoli Post Monitor task handles publishing on the post's scheduled day.

### Step 8 — Chat Reply

Keep the full written plan (Part 1 tables + Part 2 posts + article suggestion). State clearly which posts were auto-approved/queued (with day/time) and which are still pending because they need an image. Remind the human that the desktop app needs to be open on weekday mornings for the Post Monitor to run, and that any queued post can still be edited or unapproved in the dashboard's "This Week" tab before its post date.

## Output Format

Plain text, no em dashes. Each post: day/date/time, platforms (Facebook + Instagram), property, type, image URL (real, fetched, or a clear note that one is needed), full caption under 300 words ending "Book direct: rivolistays.co.uk | Link in bio" with #RivoliStays plus 4-6 targeted hashtags.

## Dashboard Boundary Rule

Do **not** touch the separate `rivoli-seo-dashboard` artifact from this workflow — it's owned and rewritten daily by a different task (`rivoli-seo-daily-rescan`) and wipes its own Content Plan tab every morning. The **Rivoli Social Dashboard** (`rivoli-social-dashboard`) is the single source of truth for the weekly post plan, since it self-syncs live from the data store on every load.

## Related

- [[06-Social-Media-Content-Strategy]]
- [[09-Automation-Architecture-Make]]
- [[14-Rivoli-Social-Dashboard-Reference]]
- [[15-SEO-Article-Pillars]]
