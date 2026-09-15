---
title: KPIs
tags: [rpm, kpi, metrics]
updated: 2026-09-15
---

# KPIs

Landlord acquisition is a lead-generation funnel, not a booking funnel, so the metrics differ from Rivoli Stays:

- Enquiry/contact-form submissions attributed to social (UTM-tagged links in bio/posts)
- Click-through rate to the landlord enquiry page, by pillar
- Follower growth per platform, with LinkedIn weighted most heavily given the audience fit
- Engagement rate by pillar (which content actually gets landlords commenting/sharing vs. scrolling past)
- Testimonial reuse rate — whether the same 2–3 stories are carrying the whole library, signalling a need for more case studies (currently moot: the library has zero entries, see [[16 - Case Study Library]])

## UTM convention (set 5 September 2026)

- `utm_source={platform}` (facebook / instagram / linkedin)
- `utm_medium=social`
- `utm_campaign=rivoli_management`
- `utm_content={post id}` — the same `id` already in the record schema, e.g. `rm-001`
- Appended to `rivolipropertymanagement.co.uk/#contactus`

This maps directly onto existing record fields (`id`, `platforms`), so no new data-store field was needed. **Not yet wired into any live generation logic** as of the last confirmed check — worth verifying whether the weekly content-draft task is actually appending these tags when it writes each record.

## Related

[[04 - Content Strategy]] · [[06 - Data Model]] · [[11 - Rollout Status]]
