---
title: Dashboard (Rivoli Management Command Centre)
tags: [rpm, dashboard, artifact]
updated: 2026-09-15
---

# Dashboard — "Rivoli Management Command Centre"

## What it is and where it lives

The live, canonical dashboard is a **published Claude Artifact** titled **"Rivoli Management Command Centre"**:

`https://claude.ai/code/artifact/2436f771-3e95-47b1-8fa2-3e7df81b1322`

This superseded an earlier plan (and an earlier build attempt) to ship it as a static file inside `C:\Users\Stuart.Mann\Claude\Artifacts\`, synced via the Cowork-desktop-only `window.cowork.callMcpTool` mechanism (the way the original `rivoli-social-dashboard` works). That earlier local-file version (`rivoli-management-social-dashboard/index.html`) is now **redundant and should be disregarded**.

The published-Artifact version instead uses the Artifact platform's own MCP capability (`window.claude.use('mcp')` → `mcp.callTool(...)`), which:

- works from any device/browser, not just the desktop app with a folder connected;
- is fully store-driven — nothing about the weekly schedule is hardcoded, it renders whatever `brand: "RM"` records are currently in the shared store, so it never goes stale;
- works around native `confirm()`/`alert()` dialogs being blocked inside the Artifact's sandboxed iframe, by rendering its own in-page confirmation UI for anything needing a human "yes, I've checked this" (the JPEG-format check, and review confirmation for a post whose claims didn't auto-verify).

## Tabs

| Tab | Purpose |
|---|---|
| Dashboard | Follower counts (FB, IG, LinkedIn), recent posts, pending count |
| This Week / Upcoming Posts | Review/approve/edit this week's plan; "requires review" badge distinct from "pending — needs image" |
| Post History | Filterable post archive, filterable by pillar as well as platform; each posted row should link directly to the live post via `posted_urls` — currently unpopulated, see [[13 - Reliability Incidents]] |
| Case Study Library | View/add testimonials and case studies, track consent; flags any testimonial nearing overuse (3+ posts). Currently empty — see [[16 - Case Study Library]] |
| Events / Market Calendar | Landlord-relevant dates — legislative milestones, market data releases, competitor activity |
| Strategy Insights | Engagement by pillar/platform, same pattern as the Stays dashboard but split by pillar instead of property |

## Architecture notes (for future edits)

- `DATA_STORE_ID = 129528`, `BRAND = 'RM'`, MCP server name `'Make'`.
- `getMcp()` lazily resolves `window.claude.use('mcp')`.
- `mapPostRecord(d, key)` and `mapCaseStudyRecord(d)` normalize raw store records.
- `initFromDataStore()` fetches with `{ dataStoreId, limit: 100 }` and filters `rec.data.brand === BRAND` client-side — the data store has **no server-side filter**.
- `approvePost(id, skipConfirm)` re-reads live state before writing (a lost-update guard) and renders its own `showWarn`/`hideWarn` in-page confirmations instead of native `confirm()`.
- `addCaseStudy()` writes via `data-store-records_create`.
- **Known limitation, documented in-code:** the 100-record page cap on `data-store-records_list` will start silently dropping RM records once the shared store (currently 57+ records combined RS+RM) grows past 100. Worth revisiting before that happens.
- The dashboard's Strategy Insights tab previously had **hardcoded, stale bullet text** (claims about zero posts published, LinkedIn not working, etc. that were true when first written but became false as the pipeline went live). This was found and fixed (15 September 2026) — the insights are now computed dynamically from the live data (post counts, which platforms have actually been used, LinkedIn posted-count, case study count) rather than hardcoded strings. Republished as **Version 8** of the artifact.

## Related

[[05 - Technical Architecture]] · [[06 - Data Model]] · [[15 - Post Log (Live and Queued)]] · [[16 - Case Study Library]]
