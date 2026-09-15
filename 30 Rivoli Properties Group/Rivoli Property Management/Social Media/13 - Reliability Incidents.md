---
title: Reliability Incidents and Fixes
tags: [rpm, reliability, incidents, makecom]
updated: 2026-09-15
---

# Reliability Incidents and Fixes

These originated from Stuart's question (5 September 2026) about whether the system needed to be more scalable, which surfaced a real, diagnosable problem rather than a general worry.

## 1. LinkedIn caption-length failures (Rivoli Stays)

Pulling execution history for Rivoli Stays' live "Integration LinkedIn" scenario (Make scenario ID 5969045) showed **22 failed executions out of 33 total**, every one with the identical error:

```
400: com.linkedin.content.common.exception.BadRequestResponseException:
ShareCommentary text length (4318–4807 characters, varying by execution)
exceeded the maximum allowed (4000 characters)
```

Not a Make.com capacity/plan-tier problem — a missing content-validation step. The repeated "start/stop" events were Stuart manually re-running after each failure, which inflated the raw failure count (several were retries of the same over-length caption).

**Confirmed platform caption limits:**

| Platform | Confirmed limit | Source |
|---|---|---|
| LinkedIn (organisation post, API) | 4,000 characters (hard reject) | Live error data from scenario 5969045, 4 Sept 2026 |
| Instagram caption | 2,200 characters | Published platform guidance, checked 5 Sept 2026 |
| Facebook page post | 63,206 characters (not a practical constraint) | Published platform guidance, checked 5 Sept 2026 |

**Stopgap fix applied to Rivoli Stays (5 September 2026):** scenario 5969045's content mapper changed from a raw pass-through to:

```
{{if(length(2.text) > 4000; substring(2.text; 0; 4000); 2.text)}}
```

This truncates hard at the character boundary (potentially mid-sentence) rather than regenerating or flagging for rewrite — it stops the failure pattern but is not the full fix. Recommend watching real executions to confirm no truncated post reads badly.

**Requirements this created for Rivoli Management (build-in, not retrofit):**

1. Validate caption length at generation time, before a record ever reaches the queue — enforced structurally by the `caption_length_ok` field (see [[06 - Data Model]]).
2. Capture proof of posting (real post ID/URL from the platform API), not just a status flag — the `posted_urls` field. **Still not achieved** — see below.
3. A bigger Make.com plan is not the fix for what's currently broken and isn't needed to launch RM — revisit only once both brands are posting in parallel and actually hit the Free plan's 1,000 ops/month or 2-active-scenario caps in practice.

## 2. The Free-plan 2-active-scenario cap incident

**5 September 2026.** Make's Free plan caps the account at 2 simultaneously active scenarios (confirmed via API: `license.scenarios: 2`). While building/testing scenario 7257618, it briefly became a 3rd active scenario alongside Rivoli Stays' two live ones (5969045, 5857917) — Make **silently deactivated the oldest**, which happened to be Rivoli Stays' live Facebook/Instagram poster (5857917). Caught by re-checking `scenarios_list`, not by any alert — Make does not appear to notify when this happens.

**Fixed immediately:** 7257618 deactivated, 5857917 reactivated.

**Decision (Stuart, 5 September 2026): toggle manually as needed** — activate whichever scenario is about to run, deactivate it after. No plan upgrade, no consolidation.

**Ongoing risk accepted:** if a toggle step fails partway (crashes after activating but before deactivating, or vice versa), a scenario could get stuck in the wrong state until someone notices. Worth a periodic sanity check once any automated monitor is running.

## 3. First live test post — router filter didn't work

**5 September 2026.** The scenario was originally built with a Router splitting into three filtered branches (Facebook/Instagram/LinkedIn), gated on `{{4.platforms}}` containing that platform's name. Two live test attempts both returned 200 "Accepted" but produced only 1 Make operation each — the trigger fired but none of the platform filters ever matched, so nothing posted. Root cause not fully confirmed (most likely an array-vs-text comparison issue), not debugged further under live-fire conditions.

**Fix applied:** removed the Router and its filters entirely. Scenario 7257618 now posts unconditionally to all three platforms on every call. Re-tested: 4 operations, ~18.6 second run, success — consistent with three real platform API calls plus the trigger.

This was later confirmed (10 September 2026) to be the **intended** behaviour going forward, not a defect to fix — see [[14 - Operational History Log]] §14.4.

## 4. `posted_urls` — still unsolved

Requirement 2 above (capture the real post URL/ID) is not achievable on the current Make API tier: execution detail only returns a bare success/failure status, not per-module input/output. Confirming exact post links currently means checking each page manually. A future fix would need a step that writes each module's own returned Post ID into the webhook response — not yet built.

## Related

[[05 - Technical Architecture]] · [[06 - Data Model]] · [[14 - Operational History Log]] · [[08 - Dashboard (Command Centre)]]
