---
title: Rivoli Stays - LinkedIn Publishing Rules
tags: [rivoli-stays, linkedin, automation, technical]
aliases: [LinkedIn Rules, LinkedIn Automation]
---

# Rivoli Stays — LinkedIn Publishing Rules

## Scenario and Webhook

- **Scenario:** "Rivoli Stays - Integration LinkedIn" (Make.com ID `5969045`, team `1767102`, hook ID `3138718`)
- **Webhook URL:** `https://hook.eu1.make.com/pf9pb6uvv8yk6qh0t5767obahohvlssq`
- **Connection:** SJM LinkedIn (connection ID `7836576`/`7837395`, Stuart Mann OpenID), scopes `rw_organization_admin` + `w_organization_social`, valid to 2027-05-30
- **Publishes to:** Rivoli Stays LinkedIn company page, `urn:li:organization:109512382`, via `CreateCompanyImagePost`
- **Payload fields:** `text` (full post including hashtags), `title` (5-8 word image alt text), `image_url`

## Hard Character Limit — 3990 Characters

Every LinkedIn post sent to the webhook must be **under 3990 characters total** (full text including hashtags and URL). LinkedIn's `ShareCommentary` API rejects anything over 4000 characters with a 400 `DataError`, which fails the Make scenario execution.

This publishes as a LinkedIn **company post** (`CreateCompanyImagePost`), not a true long-form LinkedIn Article — so the 4000-character cap applies even to "article"-style weekly content. When drafting a weekly LinkedIn write-up, cap it at roughly **550-600 words** (~3900 characters) regardless of any brief that asks for a longer word count.

**Always count the full character length before sending to the webhook.**

## Image URLs — Must Be Direct CDN Links

LinkedIn's API cannot follow redirects. The Unsplash redirect format `source.unsplash.com/1200x628/?keyword` redirects to a CDN image, and LinkedIn rejects it with a `DataError` ("Data couldn't be processed").

**Always use the direct CDN format:** `https://images.unsplash.com/photo-[ID]?w=1200&q=80` (Unsplash is used for the *Rivoli Property Management* brand's LinkedIn content, which sources generic images rather than the properties' own photos — see [[16-Rivoli-Property-Management-RM-Brand]]).

## Auto-Publish, No Confirmation Needed

For the weekly Rivoli Stays LinkedIn post, publish via the webhook automatically — do not pause to ask for approval first. Compute the topic, write the post, publish, then report status (Accepted/failed). Only stop for input if publishing fails or required tools are unavailable.

## The "Accepted ≠ Published" Trap

The webhook returns "Accepted" as long as the hook exists, **even when the scenario itself is switched off**. If the scenario is inactive, posts silently queue and never publish. Always verify with `executions_list` that the newest execution status is **1 (success)** before treating a post as live. See [[09-Automation-Architecture-Make]] and [[12-Known-Issues-and-Fixes-Log]] for the recurring incidents this caused.

## Queue Behaviour — Cannot Be Drained by Reactivation

If oversized or invalid items get stuck in the webhook's queue, reactivating the scenario does **not** clear them — they simply re-fail and re-trigger Make's error threshold (`maxErrors: 3`), which auto-disables the scenario again within seconds. There is no API/MCP tool to flush a webhook queue. It must be cleared manually in the Make.com UI: **Webhooks → click the webhook → Queue tab → select-all checkbox → Delete.** This requires Stuart (or Jeanie) to be logged into eu1.make.com directly — Claude must never log in on their behalf.

## Related

- [[02-Brand-Voice-and-Messaging]]
- [[09-Automation-Architecture-Make]]
- [[12-Known-Issues-and-Fixes-Log]]
