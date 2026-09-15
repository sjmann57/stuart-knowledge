---
title: Rivoli Property Management (RM) - Social Media Rules
tags: [rivoli-stays, rivoli-property-management, brand, social-media]
aliases: [RPM, RM Brand, Rivoli Property Management]
---

# Rivoli Property Management (RM) — Social Media Rules

Rivoli Property Management is a **separate, landlord-facing brand** within the same Rivoli group — easy to confuse with Rivoli Stays but with a different audience, different image sourcing rule, and a stricter auto-approve gate. Kept here because it shares the same Make.com data store and content-ops patterns as Rivoli Stays.

## What It Is

A Rent-to-Rent and short-let-conversion offer targeting tired/accidental landlords, initially within 20 miles of DE11, centred on Burton upon Trent and Derby (possible extension to Nottingham). Being reformed (Sept 2026) as its own Ltd company under the Rivoli Properties Ltd holding company, trading as "Rivoli Property Management". Domain: `rivolipropertymanagement.co.uk` (separate from `rivolistays.co.uk`, same WordPress/Divi/GoDaddy stack).

It offers landlords two options:
- **Option 1** — the original Rent-to-Rent model: 3-5 year lease, guaranteed rent, managed by Rivoli or another operator.
- **Option 2** — helping a landlord convert an already-let property to short-term stays using Rivoli's systems, with Rivoli taking a management commission instead of a guaranteed-rent lease.

## Critical Difference From Rivoli Stays Content

**RM social content is about other people's properties and how Rivoli can help them (landlord acquisition) — not Rivoli's own portfolio.** As a direct consequence:

- **Always source images from Unsplash** for RM content, **never** from Rivoli Stays' own property photos.
- Use the **direct CDN URL format** `https://images.unsplash.com/photo-[ID]?w=1600&q=80&fm=jpg&fit=crop` — never the `source.unsplash.com` redirect format (LinkedIn/Instagram reject redirects). See [[10-LinkedIn-Publishing-Rules]].

## Stricter Auto-Approve Gate

RM posts auto-approve and publish **only when every factual, legal, or statistical claim in the caption is fact-checked to 100% confidence against a live source.** If any claim can't be fully verified, the post must wait for human review instead of auto-publishing. This is stricter than the Rivoli Stays gate (which only requires a real image — see [[13-Weekly-Content-Plan-Workflow]]), because RM content often makes claims about legislation (e.g. the Renters' Rights Act) that carry real legal/reputational risk if wrong.

## Data Store and Key Prefix

Shares the same Make.com data store (`129528`) as Rivoli Stays, distinguished by:
- Key prefix `rm-001`, `rm-002`, ... (vs. `w-0NN` for Rivoli Stays)
- A `brand: "RM"` field on each record
- An `entryType: "social_post"` field
- Additional fields not present on Rivoli Stays records: `pillar`, `platforms` (JSON array string), `sourced_claims` (JSON array of `{claim, source}` pairs), `requires_human_review`, `caption_length_ok`

## Content Pillars (RM-specific)

- **The Switch Case** — why landlords are moving from traditional letting to managed/short-let models (e.g. Renters' Rights Act changes removing Section 21).
- **Local Market Insight** — regional employment/construction news reframed as evidence of steady serviced-accommodation demand for a managed let.
- **Hands-Off Proof** — reassurance content about what "fully managed" actually means day to day (vetting, cleaning, same-day issue response).

## Dashboard

A separate "Rivoli Management Command Centre" artifact handles RM's social planning/approval, live-synced to the same data store `129528` filtered to `brand: RM`. Do not conflate this with the Rivoli Social Dashboard (`rivoli-social-dashboard`), which is Rivoli Stays-only.

## Publishing Mechanics

RM's publish scenario (Make.com ID `7257618`, webhook-triggered) posts to Facebook, Instagram, **and** LinkedIn on every run regardless of the record's `platforms` field — this is confirmed intended behaviour, not a bug. Activating it requires deactivating one of the two scenarios Rivoli Stays normally keeps active (per the 2-scenario cap — see [[09-Automation-Architecture-Make]]), running it, then deactivating it again and reactivating the swapped-out scenario.

## Related

- [[00-Rivoli-Stays-Overview]]
- [[09-Automation-Architecture-Make]]
- [[10-LinkedIn-Publishing-Rules]]
- [[13-Weekly-Content-Plan-Workflow]]
