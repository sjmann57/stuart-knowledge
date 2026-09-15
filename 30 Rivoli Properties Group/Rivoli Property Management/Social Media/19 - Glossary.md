---
title: Glossary
tags: [rpm, glossary, reference]
updated: 2026-09-15
---

# Glossary

**RPM** — Rivoli Property Management, the landlord-facing brand. See [[01 - Brand and Positioning]].

**RS** — Rivoli Stays, the guest-facing serviced-accommodation brand. RPM's infrastructure deliberately mirrors but stays separate from RS's, except for the shared data store.

**SA** — Serviced accommodation (short-term/furnished holiday-let style letting), as opposed to a traditional assured shorthold tenancy (AST).

**AST** — Assured shorthold tenancy, the traditional UK residential letting structure affected by the Renters' Rights Act 2025. See [[03 - Market Context and Legislative Drivers]].

**Option 1** — RPM's guaranteed-rent lease model: a 3–5 year lease at fixed rent, Rivoli (or another operator) manages the property.

**Option 2** — RPM's SA-conversion model: helping a landlord convert an already-let property to short-term stays, with Rivoli taking a management commission rather than a lease.

**Content pillar** — one of six recurring content themes (The Switch Case, Hands-Off Proof, Numbers That Hold Up, Compliance & Risk, Social Proof, Local Market Insight). See [[04 - Content Strategy]].

**`brand` field** — discriminator on shared data store records: `"RM"` for Rivoli Management, `"RS"` (or blank, for legacy records) for Rivoli Stays.

**`entryType` field** — discriminator on shared data store records: `"social_post"` or `"case_study"`.

**`sourced_claims`** — array of `{claim, source}` pairs attached to a post record; the mechanism that lets a claim be checked before a post can auto-approve. See [[06 - Data Model]], [[07 - Approval Governance]].

**`requires_human_review`** — boolean on a post record; `true` means it did not fully pass the fact-check gate and must wait for a human.

**`caption_length_ok`** — boolean set at generation time; blocks a record from reaching `approved` status if the caption exceeds the target platform's character limit.

**`posted_urls`** — field meant to hold the real, live post URL(s) after publishing; currently unpopulated for every RM record due to a Make API-tier limitation. See [[13 - Reliability Incidents]].

**Command Centre** — shorthand for the "Rivoli Management Command Centre" dashboard artifact. See [[08 - Dashboard (Command Centre)]].

**Manual publish recipe** — the current (non-automated) five-step process for publishing an approved post, involving toggling Make.com scenario activation around the Free plan's 2-active-scenario cap. See [[14 - Operational History Log]] §14.5.

**Free plan caps** — Make.com account limits: 1 data store, 2 simultaneously active scenarios, 1,000 operations/month.

**Renters' Rights Act 2025** — UK legislation, in force since 1 May 2026, that abolished Section 21 no-fault evictions and moved standard tenancies to periodic terms. See [[03 - Market Context and Legislative Drivers]].

**DE11** — postcode area (Swadlincote) used as the geographic centre point for RPM's landlord targeting radius (~20 miles).

## Related

[[00 - Home]]
