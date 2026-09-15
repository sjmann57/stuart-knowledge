---
title: Rivoli Stays - Website and Asset Reference
tags: [rivoli-stays, reference, website, assets]
aliases: [Website Reference, Image Assets]
---

# Rivoli Stays — Website and Asset Reference

## Key URLs

- **Main site:** https://rivolistays.co.uk/
- **Booking platform** (separate subdomain): https://www.booking.rivolistays.co.uk/
- **Properties index:** https://rivolistays.co.uk/properties/

### Individual property pages

- Nightingale (Derby DE1): https://rivolistays.co.uk/properties/nightingale/
- Mews (Burton upon Trent): https://rivolistays.co.uk/properties/mews/
- Leas (Branston, Burton upon Trent): https://rivolistays.co.uk/properties/leas/
- Brook (Burton upon Trent): https://rivolistays.co.uk/properties/brook/

## Image Assets

Hosted at `https://rivolistays.co.uk/wp-content/uploads/` organised by year/month, e.g. `2026/02/`, `2025/10/`. Pattern: `.../uploads/YYYY/MM/filename-scaled.jpg`.

**Rule for social media images: never invent a URL.** Only use an `og:image` or gallery image actually seen on a fetched property page, or one already confirmed real in the Make.com data store / Rivoli Social Dashboard from a previous week. Must be `.jpg` — Instagram rejects PNG.

### Known-good, previously confirmed real image URLs (reusable, checked against live posts)

- Nightingale: `https://rivolistays.co.uk/wp-content/uploads/2026/02/Nightingale-Living-Area-2-scaled.jpg`
- Nightingale (alt): `https://rivolistays.co.uk/wp-content/uploads/2026/02/Nightingale-Living-Area-4-scaled.jpg`
- Mews: `https://rivolistays.co.uk/wp-content/uploads/2026/02/Rivoli-Mews-Bedroom-1-5-scaled.jpg`
- Leas: `https://rivolistays.co.uk/wp-content/uploads/2026/04/Rivoli-Leas-Living-Room-3-scaled.jpg`
- Brook: `https://rivolistays.co.uk/wp-content/uploads/2025/10/Living-Room-5-scaled.jpg`
- Brook (alt): `https://rivolistays.co.uk/wp-content/uploads/2025/10/Bedroom-1-8-scaled.jpg`

Before fetching a property page for a fresh image, always check the Rivoli Social Dashboard's `POSTS`/`WEEKLY_PLAN` arrays and the Make.com data store (129528) first — reuse a confirmed-real URL for the matching property rather than re-fetching.

## Technical Notes

- Platform: WordPress, built with the Divi theme/builder (same builder used for rivolipropertymanagement.co.uk).
- Site Kit by Google plugin detected.
- reCAPTCHA on the contact form.
- A prior SEO/AI-visibility audit found: duplicate homepage content (a Divi quirk), broken internal property links, missing schema markup, testimonial reviews embedded as images (not indexable by search), and a booking subdomain that dilutes domain authority. A viewport meta tag fix was also scoped. These are open website issues, not social media issues, but relevant to overall Rivoli Stays digital presence.

## Use When

Pulling fresh property details, sourcing imagery for a post, linking to the booking flow in copy, or verifying the current property roster (which may grow over time).

## Related

- [[01-Property-Portfolio]]
- [[03-Visual-Identity]]
- [[06-Social-Media-Content-Strategy]]
