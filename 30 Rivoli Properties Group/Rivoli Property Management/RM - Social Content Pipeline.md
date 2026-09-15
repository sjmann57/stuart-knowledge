---
title: RM - Social Content Pipeline
tags: [rivoli-management, marketing]
---

# Social Content Pipeline

- A **weekly content-draft scheduled task** ("Rivoli Management weekly content draft", Mondays) drafts the next Tue/Thu/Fri posts, fact-checks claims, sources Unsplash images, and writes them to the data store below.
- **Data store:** Make.com data store `129528`, filtered to `brand=RM`.
- **Option rotation:** content rotates across [[RM - Option 1 (Rent-to-Rent)|Option 1]] and [[RM - Option 2 (STR Conversion & Management)|Option 2]], tracked via an `option` field on each record.
- **Auto-approve rule:** a post auto-approves and publishes **only** when every factual/legal/statistical claim in the caption is fact-checked to 100% confidence against a live source. If any claim can't be fully verified, the post waits for human review instead of auto-publishing.

## Related
- [[Rivoli Property Management (MOC)]]
- [[RM - Voice & Content Rules]]
- [[RM - Command Centre Dashboard]]
- [[RM - Publish Scenario Runbook]]
