---
title: Open Questions and Decisions
tags: [rpm, open-questions, decisions]
updated: 2026-09-15
---

# Open Questions and Decisions

## Resolved

1. **Page handles.** `facebook.com/RivoliPM`, `instagram.com/rivolipropertymanagement`, `linkedin.com/company/rivoli-property-management`. Posting to these RPM-branded pages, not the separate parent Rivoli Properties pages.
2. **LinkedIn access.** Stuart holds page admin rights, registered a developer app, and was granted Community Management API access (4 September 2026).
3. **Testimonials at spec time.** Zero consented testimonials on hand. See [[16 - Case Study Library]] — still true as of 15 September 2026.
4. **Landlord enquiry page.** Exists at `rivolipropertymanagement.co.uk` (contact form at `/#contactus`). See the phone-number discrepancy flagged below.
5. **Per-platform targeting "defect."** Confirmed intentional by Stuart (10 September 2026), not a bug — see [[14 - Operational History Log]] §14.4.

## Still open

- **Cross-brand editorial policy (deferred by Stuart).** Whether Rivoli Management posts should ever use a real Rivoli Stays property as a proof point, or keep the two brands fully separate editorially, is left undecided. Default posture until decided: treat the brands as editorially separate — no cross-referencing specific Stays properties.
- **RPM website rework.** The live site is single-page, Option-1-only. Adding Option 2 and a dual-option structure has not been started as of 15 September 2026. Stuart wants to review the reworked page before anything goes live.
- **Case Study Library.** Still zero entries. Blocks the Social Proof pillar entirely.
- **Daily post monitor automation.** Publishing is still a manual scenario-toggle recipe (see [[14 - Operational History Log]] §14.5); building this into a real unattended scheduled task, including safe recovery from a toggle that fails partway, is the main outstanding Phase 1 item.
- **`posted_urls` capture.** Still not solved — every live record checked so far shows an empty `{}`, a Make API-tier limitation (execution details don't expose per-module output on this plan). See [[13 - Reliability Incidents]].
- **UTM parameters wired into generation logic.** The convention is set ([[10 - KPIs]]) but it's unconfirmed whether the weekly content-draft task is actually appending these tags to links in generated captions.
- **Advertising campaign.** Not yet running — organic content comes first per Stuart's sequencing decision (see [[02 - Corporate Structure and Two-Option Offering]]).

## Noted discrepancy — not yet reconciled

Two different contact phone numbers are recorded for RPM in different sources:

- The technical spec (§12, item 4) records the landlord enquiry page's contact phone as **0330 120 0145**.
- Separately-stated context for the campaign/website gives the main contact number as **+44 330 120 0140**.

These may be the same number recorded with a typo in one source, or genuinely two different numbers (e.g. a general line vs. a campaign-tracked line). **This has not been checked against the live website or flagged to Stuart yet** — worth confirming which is correct before either number is used in new content or ad campaigns.

## Related

[[00 - Home]] · [[02 - Corporate Structure and Two-Option Offering]] · [[16 - Case Study Library]] · [[18 - Key IDs, Contacts and URLs]]
