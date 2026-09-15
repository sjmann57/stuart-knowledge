---
title: Approval Governance
tags: [rpm, governance, approval]
updated: 2026-09-15
---

# Approval Governance

## Current rule in force (since before go-live)

> A Rivoli Management post **auto-approves and is queued for publishing** only if **every** factual, legal or statistical claim in its caption has been fact-checked to 100% confidence against a live source. If any claim cannot be fully verified, the post is written as `pending` and must wait for human review — regardless of which pillar it belongs to.

In practice this means every pillar can auto-approve, provided its claims check out at generation time. Several of the 15–25 September batch are exactly this: The Switch Case and Numbers That Hold Up posts with `requires_human_review: false`, because their claims were verified against gov.uk/VisitBritain sources when generated. The dashboard still has a `requires_human_review` field and a "Requires Review" badge for whichever posts fail verification — the mechanism is unchanged, only the trigger changed (from "which pillar is this" to "did every claim check out").

Standing safeguard carried over from Rivoli Stays: the (currently manual) publishing step only fires posts already marked `approved`, and Stuart/Jeanie can edit or unapprove any post up to its scheduled time.

## Superseded original rule (kept for history — see spec §7)

The very first version of this rule, replaced before go-live, was pillar-based:

- A post auto-approved only if it had a real image **and** its pillar was pre-designated low-risk (Social Proof with a consented testimonial, or Local Market Insight with no financial claims).
- The Switch Case, Numbers That Hold Up and Compliance & Risk always required human approval, regardless of image status, if it carried `sourced_claims`.

This was replaced by the fact-check-driven rule above because it was simpler to apply consistently and didn't block genuinely well-sourced posts in the "always review" pillars.

## Why this exists

The original Rivoli Stays rule — "any post with a real image URL auto-approves" — solved a specific failure mode (weeks of nothing publishing because no one approved the plan) for low-risk, non-claim-bearing hospitality captions. Landlord acquisition content carries higher stakes if something inaccurate or overpromising goes out, so a compliance gate was added rather than carrying the Stays rule over unmodified.

## Related

[[04 - Content Strategy]] · [[06 - Data Model]] · [[09 - Compliance and Legal Guardrails]] · [[15 - Post Log (Live and Queued)]]
