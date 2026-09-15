---
title: Compliance and Legal Guardrails
tags: [rpm, compliance, legal]
updated: 2026-09-15
---

# Compliance and Legal Guardrails

These are guardrails a general marketing framework does not need but a landlord-facing, financial-services-adjacent one does.

- **No guaranteed-return language** ("guaranteed rent", "guaranteed yield") without a linked terms page, and only where that guarantee is a real contractual offer Rivoli makes — never as a figure of speech.
- **No invented statistics.** Any occupancy rate, yield percentage or revenue figure used in a post must trace to a `sourced_claims` entry with a real source (internal reporting or a cited external study). This is enforced structurally by the data model and approval rule, not just by house style — see [[06 - Data Model]] and [[07 - Approval Governance]].
- **Testimonial consent is tracked, not assumed.** A testimonial cannot be used in a post unless `landlordConsentOnFile` is `true` in the case study library record — see [[16 - Case Study Library]].
- **Advertising standards awareness.** Content that could read as a financial promotion (implying investment returns) should get a second read against ASA/CAP code guidance before publishing. Flag this explicitly for any Numbers That Hold Up post; consider a standing disclaimer line for that pillar.
- **GDPR.** Landlord names, quotes and photos in the case study library are personal data — store only what's needed, and honour any consent-withdrawal request by removing the record entirely, not just unpublishing the post it was last used in.

## Legislative context these guardrails respond to

See [[03 - Market Context and Legislative Drivers]] for the Renters' Rights Act 2025 and the pending short-term-let registration scheme — both are exactly the kind of claim that must be sourced and dated before use.

## Related

[[06 - Data Model]] · [[07 - Approval Governance]] · [[16 - Case Study Library]] · [[03 - Market Context and Legislative Drivers]]
