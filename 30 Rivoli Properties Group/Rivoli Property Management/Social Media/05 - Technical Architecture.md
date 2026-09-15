---
title: Technical Architecture
tags: [rpm, architecture, makecom, technical]
updated: 2026-09-15
---

# Technical Architecture

## Design principle

Mirrors the proven Rivoli Stays pattern — weekly content generation → dashboard review → Make.com data store → post publish — because it already works and Stuart is already familiar with it. Every component is newly named and newly provisioned so the two systems cannot cross-contaminate, with **one deliberate exception: the Make.com data store itself.**

The existing "RS Data Store" (129528) holds live, real Rivoli Stays post history — not an unused resource — and Make's Free plan hard-caps the account at **one data store, full stop** (confirmed by a failed creation attempt, at any size). Rather than pay to raise that cap or risk overwriting real data, both brands share this one store: its data structure was extended with `brand` (RS/RM) and `entryType` (social_post/case_study) fields so both brands' records coexist safely, filtered apart at the scenario and dashboard level. See [[06 - Data Model]] for the full schema.

## Components

| Component | Rivoli Stays (existing, untouched) | Rivoli Management (new) |
|---|---|---|
| Make.com data store | ID 129528, structure "Rivoli Social Post + Case Study (RS + RM, shared)" (id 460017) | **Shared, not new** — same store/structure, extended with `brand`/`entryType`. Every RM module must filter/write with `brand = "RM"` |
| Posting scenario | Publishes to Rivoli Stays FB/IG (scenarios 5857917, 5969045) | Scenario **7257618**, "Rivoli Management — Publish to Social Media." Posts unconditionally to Facebook, Instagram and LinkedIn on every webhook call (see [[14 - Operational History Log]] §14.4 for why the originally-planned per-platform router was removed) |
| Webhook | Existing Stays webhook | Webhook id **3668582**, `https://hook.eu1.make.com/5xkwoebixcijmudlbjbb80hua4tski8t`, feeds scenario 7257618 with `{caption, image_url, platforms}` |
| Dashboard artifact | `rivoli-social-dashboard` | Published Claude Artifact, **"Rivoli Management Command Centre"** — see [[08 - Dashboard (Command Centre)]] |
| Weekly content-plan task | `rivoli-weekly-content-plan` | **"Rivoli Management weekly content draft"**, runs Mondays — see [[04 - Content Strategy]] |
| Daily post monitor | `Rivoli Post Monitor` | **Not yet built as an unattended task.** Publishing runs via a manual recipe — see [[14 - Operational History Log]] §14.5 |

## Platform connection details

- **Facebook branch:** connection 7633808 (admins both RivoliPM and Rivoli Stays pages), page id `647855118415654`.
- **Instagram branch:** same connection, account id `17841475222097939` (`@rivolipropertymanagement`).
- **LinkedIn branch:** connection 7837395, organisation `urn:li:organization:146275272` ("Rivoli Property Management" — distinct from "Rivoli Properties" `urn:li:organization:104753708`, and from Rivoli Stays' own `urn:li:organization:109512382`). Has a length-truncation guardrail matching the fix applied to Rivoli Stays' LinkedIn scenario (see [[13 - Reliability Incidents]]).

## LinkedIn-specific build notes

LinkedIn organisation posting required a two-tier, manually-reviewed Community Management API approval process (not self-serve):

- **Development tier:** verified business email, organisation's legal name/address/website/privacy policy, LinkedIn Page super-admin verification of the app.
- **Standard tier** (needed before live posting): a full working integration plus a screen recording demonstrating the OAuth flow, posting to the page, and how comments/commenter data are displayed.
- LinkedIn does not allow re-applying with a rejected app — a bad first submission means starting over with a new app.
- OAuth scope for organisation posting: `w_organization_social`.
- **Outcome:** access was requested and granted the same day it was raised (4 September 2026) — faster than the multi-week risk originally flagged.
- LinkedIn image posts require the image to be uploaded via a separate "register upload" API call before the post is created — a different flow from Meta's Graph API (which accepts an image URL directly), hence a distinct LinkedIn branch in the scenario rather than a shared "post to all platforms" step.

## Data flow (as designed)

1. **Weekly generation** (Mondays) — researches, drafts posts, sources images, fact-checks claims, writes records to the shared store tagged `brand: "RM"`, `entryType: "social_post"`.
2. **Human review** — via the dashboard's This Week/Upcoming Posts tab: approve, edit, or leave pending. Auto-approval logic is in [[07 - Approval Governance]].
3. **Publishing** — currently a manual recipe (not yet an unattended daily monitor): reads approved records with a post date due, publishes via scenario 7257618, marks the record `posted` with a timestamp. `posted_urls` capture is not yet solved (see [[13 - Reliability Incidents]]).
4. **Dashboard** — re-syncs live from the data store on every load, filtered to `brand = "RM"` so Stays' records never appear and vice versa.

## The Free-plan 2-active-scenario cap

Make's Free plan caps the account at **2 simultaneously active scenarios** (same tier that caps it at 1 data store). Rivoli Stays' two scenarios (5969045 LinkedIn, 5857917 Meta) normally hold both slots, so scenario 7257618 cannot simply run alongside them — see [[13 - Reliability Incidents]] for the incident this caused and the manual-toggle decision that resulted.

## Related

[[06 - Data Model]] · [[07 - Approval Governance]] · [[08 - Dashboard (Command Centre)]] · [[13 - Reliability Incidents]] · [[18 - Key IDs, Contacts and URLs]]
