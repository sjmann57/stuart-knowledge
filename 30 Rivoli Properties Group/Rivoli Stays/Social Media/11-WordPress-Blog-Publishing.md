---
title: Rivoli Stays - WordPress Blog Publishing
tags: [rivoli-stays, wordpress, blog, automation, seo]
aliases: [Blog Publishing, WordPress Automation]
---

# Rivoli Stays — WordPress Blog Publishing

## Scenario

- **Name:** Rivoli Stays — Publish Blog Article
- **Scenario ID:** `5868161`
- **Type:** On-demand (not webhook-triggered from outside, but has its own internal 15-minute polling schedule — see the deduplication warning below)
- **WordPress connection ID:** `7650569` (`accountName: wordpress4`)
- **Webhook URL (legacy/alternate trigger):** `https://hook.eu1.make.com/hyrmfgy6hvvmcjyo8gh6khmeawvmo52d` with payload fields `title`, `content` (HTML), `excerpt`, `slug`

## Publishing Pattern (critical — template variables don't work)

Do **not** use `{{input.*}}` template variables in the Make mapper — they silently fail. The correct pattern is:

1. **Update** the blueprint with the article content hardcoded directly into the mapper (via `scenarios_update`).
2. **Run** the scenario (`scenarios_run`, `responsive: true`).
3. **Verify** via `executions_get-detail` that `status: "SUCCESS"`.

### Field values

- Post type (`type`): `"posts"` — not `"post"` (the WordPress API expects the plural).
- Publish status (`status`): `"publish"` (goes live immediately).

### Activation dance (2-scenario cap)

Because the Make account caps active scenarios at 2 (see [[09-Automation-Architecture-Make]]), and the two social scenarios (`5969045` LinkedIn, `5857917` Facebook/Instagram) are normally both active, publishing a blog article requires:

1. Deactivate one social scenario (e.g. `5857917`) to free a slot.
2. Activate `5868161`.
3. Run it.
4. Deactivate `5868161` again.
5. Reactivate the social scenario from step 1.
6. Confirm via `scenarios_list` that the two social scenarios are back to active and the blog scenario is inactive.

`scenarios_run` can fail with "Scenario is not activated" if attempted while inactive — it must be briefly activated to run, unlike some other Make behaviours.

## Deduplication — Critical Fix

Scenario `5868161` has its **own internal scheduled trigger** (`interval: 900`, every 15 minutes). If left active after a manual run, Make's own schedule re-fires the same hardcoded blueprint content repeatedly, creating duplicate WordPress posts.

**Fix implemented:**

1. A weekly blog task reads a lock file (`blog_publish_log.txt` in the project folder) and skips the entire run if the current `YYYY-Www` key is already recorded.
2. After a successful publish, the task **deactivates** scenario `5868161` again to stop its internal scheduler from re-firing.
3. The task then writes the lock file with the current week key.

`scenarios_run` still works on an inactive scenario (a manual trigger bypasses active/inactive state), so this doesn't block future scheduled runs.

## Weekly Topic Rotation

Scheduled task `rivoli-weekly-blog-article`, runs Mondays 8am UK time. Topic determined by ISO week number modulo 4:

- **1** → Local area guide (Derby if `(week//4) % 2 == 0`, else Burton)
- **2** → Corporate/contractor accommodation
- **3** → Property showcase (further rotated by `week//4 % 4`: 0 = Nightingale, 1 = Mews, 2 = Leas, 3 = Brook)
- **0** → Guest tips / hosting standards

See also the four SEO content pillars used for both the blog and the weekly social plan's article suggestion in [[15-SEO-Article-Pillars]].

## Related

- [[09-Automation-Architecture-Make]]
- [[12-Known-Issues-and-Fixes-Log]]
- [[15-SEO-Article-Pillars]]
