---
title: Data Model
tags: [rpm, data, schema, makecom]
updated: 2026-09-15
---

# Data Model

Both schemas below live in the **same shared Make.com data store (129528)** as Rivoli Stays' existing post records — not a separate store. See [[05 - Technical Architecture]] for why. Two fields make the sharing safe:

- `brand` — every RM record must set this to `"RM"`. Rivoli Stays' original 47+ records predate this field and are blank, treated as Stays by default.
- `entryType` — `"social_post"` for the schema below, `"case_study"` for the case-study/testimonial schema.

## Social post record (`entryType: "social_post"`)

```json
{
  "id": "rm-001",
  "entryType": "social_post",
  "brand": "RM",
  "day": "Tuesday",
  "date": "8 September 2026",
  "isoDate": "2026-09-08",
  "time": "09:00",
  "timeLabel": "9:00am",
  "platforms": ["linkedin", "facebook"],
  "pillar": "The Switch Case",
  "property": "General / Brand",
  "option": "1 or 2 — added 10 Sept 2026, not in the original spec schema",
  "caption": "string",
  "image_url": "string or empty",
  "linkedin_asset_urn": "string or empty (populated after LinkedIn image upload step)",
  "sourced_claims": [
    { "claim": "Section 21 no longer available for standard ASTs from May 2026", "source": "https://en.wikipedia.org/wiki/Renters%27_Rights_Act_2025" }
  ],
  "requires_human_review": true,
  "caption_length_ok": true,
  "status": "pending | approved | posted | missed | skipped",
  "approvedAt": "ISO timestamp or empty",
  "postedAt": "ISO timestamp or empty",
  "posted_urls": "{} or {\"linkedin\": \"https://...\", \"facebook\": \"https://...\"}"
}
```

Notes:

- `sourced_claims` and `requires_human_review` are new relative to the Rivoli Stays schema and exist specifically because landlord content makes factual/financial claims that guest-facing property showcases do not. They are the mechanism that prevents an ungrounded statistic from auto-publishing.
- `caption_length_ok` is set by a validation step at generation time, before a record is ever written to the queue. `false` blocks the record from reaching `approved` status regardless of pillar or image status.
- `posted_urls` is meant to be populated from each platform's own API response after a successful post — in practice it has stayed an empty `{}` on every live record checked so far, a Make API-tier limitation (see [[13 - Reliability Incidents]]).
- `platforms` is kept in the schema and shown in the dashboard as the *intended* audience for editorial purposes, but does **not** actually filter which channels receive the post — every approved record currently posts to all three platforms regardless (confirmed intentional by Stuart, 10 September 2026 — see [[14 - Operational History Log]] §14.4).
- All fields except `entryType` and `brand` were added directly to the shared data structure on 5 September 2026 (Make data structure id 460017).

## Case study / testimonial record (`entryType: "case_study"`)

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

Consent status is tracked centrally here — see [[16 - Case Study Library]] for current status (empty, zero records as of 15 September 2026) and [[09 - Compliance and Legal Guardrails]] for the consent rule.

## Key identifiers

- Data store ID: **129528**
- Data structure ID: **460017** ("Rivoli Social Post + Case Study (RS + RM, shared)")
- Discriminator fields: `brand` (`RS` / `RM`, blank = legacy Stays), `entryType` (`social_post` / `case_study`)

## Related

[[05 - Technical Architecture]] · [[07 - Approval Governance]] · [[15 - Post Log (Live and Queued)]] · [[16 - Case Study Library]]
