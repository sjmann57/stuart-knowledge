---
title: Image Sourcing Policy
tags: [rpm, images, unsplash, policy]
updated: 2026-09-15
---

# Image Sourcing Policy

## The rule

Rivoli Management content is about **other people's properties** and how Rivoli can help them (landlord acquisition) — not Rivoli's own portfolio. It must **never reuse Rivoli Stays' real property photography**.

**Every image for Rivoli Management content is sourced from Unsplash** (`unsplash.com`) instead. This has been confirmed and reconfirmed by Stuart as standing policy.

## Correct URL format

Use the direct CDN image link, not the page link:

- **Correct (usable by platform APIs):** `https://images.unsplash.com/photo-<id>?w=1600&q=80&fm=jpg&fit=crop`
- **Incorrect (not a usable image URL):** `https://unsplash.com/photos/<slug>-<id>` (this is a page URL, not an image asset)

## Enforcement

This is enforced by the weekly content-draft task when it sources an image for each post, and is documented directly in the dashboard's source. All image URLs seen in the live/queued post log ([[15 - Post Log (Live and Queued)]]) follow the correct `images.unsplash.com/photo-...` pattern.

## Why this exists

Rivoli Stays' photography represents Rivoli's own managed properties. Using it in Rivoli Management (landlord acquisition) content would misrepresent whose property is being shown, and blurs a brand separation Stuart wants kept clean — see [[01 - Brand and Positioning]].

## Related

[[04 - Content Strategy]] · [[06 - Data Model]] · [[15 - Post Log (Live and Queued)]]
