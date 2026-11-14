---
name: read-link-analytics
description: Read linked.is click analytics for one short link or a whole workspace and summarize the result. Use when the user asks how a link or account is performing.
---

# Read link analytics

Use `get_link_analytics` on the linked.is MCP server. It needs `LINKEDIS_API_TOKEN`. It is read only.

## How to call it

- One link: pass `linkId` from `list_links` or `search_links`. Find the link first when the user gives a slug or destination instead of an id.
- Whole workspace: omit `linkId`. Omit `teamId` for the personal workspace. Pass `teamId` only for a team they belong to.
- Date range: pass `start` and `end` as ISO 8601 when the user names a range. Otherwise leave them unset. The default is the last 30 days.

The result includes `totalClicks`, `countries`, `referrers`, and `sources` (`utm_source`). A single link also includes devices and browsers. Visits with no referrer are omitted.

## How to summarize

Lead with the click total and the range. Then name the top countries, referrers, and sources with their counts. Quote only numbers that are in the tool result. If the total is zero, say the link or workspace had no clicks in that range instead of guessing a cause.
