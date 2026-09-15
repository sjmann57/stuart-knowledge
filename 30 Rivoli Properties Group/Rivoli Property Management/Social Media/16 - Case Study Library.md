---
title: Case Study Library
tags: [rpm, case-studies, testimonials]
updated: 2026-09-15
---

# Case Study Library

## Status: empty

**Zero consented landlord testimonials or case studies on hand as of 15 September 2026.** This has not moved since 4 September 2026 and remains the single biggest open Phase 0 item — see [[11 - Rollout Status]].

## Why it matters

- The **Social Proof** content pillar ([[04 - Content Strategy]]) cannot produce any content until the library has entries. The live weekly content-draft task is drawing from the other five pillars instead.
- Testimonials and case studies are meant to be reused across many posts over months, which is why this is a **maintained library**, not something re-sourced from scratch each week the way Rivoli Stays opportunistically reuses property photography.

## Schema (shared data store, `entryType: "case_study"`)

```json
{
  "id": "cs-001",
  "entryType": "case_study",
  "brand": "RM",
  "landlordFirstName": "string",
  "landlordConsentOnFile": true,
  "consentDate": "ISO date",
  "propertyArea": "Derby | Burton upon Trent | other",
  "quote": "string",
  "metricsIfAny": { "metric": "string", "value": "string", "source": "internal / verified" },
  "photoUrl": "string or empty",
  "photoConsent": true,
  "lastUsedInPostId": "rm-xxx",
  "usageCount": 0
}
```

Full field detail: [[06 - Data Model]].

## Consent policy

- A testimonial cannot be used in a post unless `landlordConsentOnFile` is `true`.
- Photo use requires separate `photoConsent`.
- GDPR: honour any consent-withdrawal request by **removing the record**, not just unpublishing the post it was last used in. See [[09 - Compliance and Legal Guardrails]].

## Dashboard support

The Command Centre dashboard has a dedicated **Case Study Library** tab (view/add testimonials, track consent) and is designed to flag any testimonial nearing overuse (3+ posts) once entries exist. See [[08 - Dashboard (Command Centre)]].

## Next step

Gather the first 3–5 real, consented landlord testimonials — this is a manual sourcing task, not something the content pipeline can generate.

## Related

[[04 - Content Strategy]] · [[06 - Data Model]] · [[09 - Compliance and Legal Guardrails]] · [[11 - Rollout Status]]
