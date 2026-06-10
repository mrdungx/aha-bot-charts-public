# aha-bot-charts-public

Chart PNGs from AhaSlides analytics routines. Sibling of the private `mrdungx/aha-bot-charts` repo.

> [!CAUTION]
> ## DO NOT make this repository private.
>
> Slack renders the PNGs in this repo via **unauthenticated** `raw.githubusercontent.com/mrdungx/aha-bot-charts-public/...` URLs. The Slack `image` block can't pass an auth token.
>
> Flipping this repo to private will break every Slack message — past and future — that references a chart here. They'll all return HTTP 404 to Slack's image fetcher.
>
> **If you need to take down a specific chart**, delete just that file (or rewrite history for that path). Don't change the repo's visibility.

## Architecture

| Repo | Visibility | Contents |
|---|---|---|
| [`aha-bot-charts`](https://github.com/mrdungx/aha-bot-charts) | **PRIVATE** | Payloads, Metabase data, workflows, internal IDs |
| `aha-bot-charts-public` (this one) | **PUBLIC** | Chart PNGs only |

Routines (managed at <https://claude.ai/code/routines>) upload PNGs here using a fine-grained PAT scoped to `Contents:write` on this repo only. The PNGs are aggregate weekly metrics (adoption rates, ranking tables) with no PII — safe to be public.

## What's safe to add here

✅ Chart images derived from aggregate metrics.

❌ Raw Slack payloads (JSON). ❌ User IDs, emails, or names. ❌ Internal Jira ticket bodies. ❌ Mixpanel raw event exports. ❌ Workflow files containing SQL or API patterns.

If you're adding a new chart, ask yourself: *would I be uncomfortable if a competitor saw this PNG?* If yes — don't post it here. If no — go ahead.

## Why this split exists

In June 2026 the sibling private repo was briefly flipped public, exposing sensitive content. That triggered a chart-vs-data split. Keep the boundary: PNGs here, everything else there.
