---
title: Corporate Structure and Two-Option Offering
tags: [rpm, strategy, corporate]
updated: 2026-09-15
---

# Corporate Structure and Two-Option Offering

## Corporate reform (September 2026)

Rivoli Property Management is being reformed as its **own Ltd company** under the **Rivoli Properties Ltd** holding company, rather than remaining a sub-brand of Rivoli Stays Ltd. It keeps the "Rivoli Property Management" trading name. The Ltd company itself is formed when the **first management deal signs** under the new structure — not before. Timeline is ASAP: signing management deals under this offering is described as an urgent business driver.

## The two options

RPM now offers landlords a choice between two distinct models, and content is deliberately rotated across both (each social-post record carries an `option` field tracking which offer it's pushing — see [[06 - Data Model]]):

- **Option 1 — guaranteed-rent lease (the original model).** A 3–5 year lease at a fixed rent, under which Rivoli (or another operator) manages the property. This is the model the original technical spec (§1) was written around, and the only option live on the current website.
- **Option 2 — conversion to short-term-stay management.** Helping a landlord convert an already-let property to short-term stays using Rivoli's systems and processes, with Rivoli taking a **management commission** rather than a guaranteed-rent lease.

Both options require the landlord to deliver a **vacant property** — arranging that (e.g. ending an existing tenancy) is the landlord's responsibility, not Rivoli's, under either option.

Option 2 targeting uses Rivoli Stays' existing guest-demand avatar (contractors/business travellers near major regional employers — Rolls-Royce, Alstom, Toyota, the Burton Towns Fund pipeline) as a baseline for judging property/location fit, but can widen to a leisure/tourism avatar depending on the specific location.

## Website and funnel

- Domain: `rivolipropertymanagement.co.uk` — already owned, self-hosted WordPress on GoDaddy hosting (not WordPress.com), built with the Divi theme/builder (same stack as rivolistays.co.uk).
- Current live site (checked 10 September 2026) is a **single page** (Home / Benefits / About Us / How It Works / Contact) covering **only Option 1**. It needs reworking to add Option 2 and a dual-option structure. **This rework has not been started as of 15 September 2026.**
- Site structure decision: **one shared enquiry funnel** presenting both options, rather than two separate paths — though individual ad campaigns may be built to steer toward a preferred option.
- Conversion goal at this stage is a **call or message**, not a form fill or booking link.
- Stuart wants any reworked page built and shown to him for review before anything goes live.

## Advertising plan (not yet running as of 15 September 2026)

- Channels: Facebook/Instagram first, Google Ads later, LinkedIn still under evaluation.
- Budget: starts at £10/week, increasing to £20/week.
- Sequencing: **organic-first** — Stuart wants general unpaid social posts pushed out before any paid ad spend. Paid ads are "Stage 2b" of the content workflow below, coming once organic messaging is established.

## The "rivoli-property-management" skill

A dedicated skill was built (10 September 2026) covering a two-stage workflow:

1. **Stage 1 — landlord lead triage and reply drafting.** Currently a manual process Stuart runs himself; the skill assists rather than decides, and he'll refine it with real operational learnings over time.
2. **Stage 2 — content generation, organic-first.** This is what the weekly content-draft scheduled task does (see [[04 - Content Strategy]] and [[14 - Operational History Log]]) — it was updated 10 September 2026 to rotate content across both Option 1 and Option 2. Stage 2b (paid ads: FB/IG → Google → LinkedIn) comes later.

## Related

[[01 - Brand and Positioning]] · [[04 - Content Strategy]] · [[11 - Rollout Status]] · [[12 - Open Questions and Decisions]]
