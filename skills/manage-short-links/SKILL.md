---
name: manage-short-links
description: Create, find, update, and delete linked.is short links, including UTM parameters and custom domains. Use when the user wants a short URL, a slug, or a change to a link they already own.
---

# Manage short links

Use the linked.is MCP server from this plugin. Account tools need `LINKEDIS_API_TOKEN`. If that variable is empty, only the free tools exist. Say so and use `free_shorten_url` only when an anonymous link with no stats is enough.

## Create

1. Call `list_domains` when the user names a custom domain or asks which hosts they can use. Pass `domain` to `shorten_link` only when that row has `available: true`. Omit `domain` to use linked.is.
2. Call `shorten_link` with the destination URL. Add `slug` or `title` only when the user asked for them.
3. Put campaign tags on the link with `utmSource`, `utmMedium`, and `utmCampaign`. Those three are stored and appended when someone opens the short link. `utm_term` and `utm_content` are not stored. Build those with `utm_link`, then shorten the result if they want a short URL.
4. Pass `teamId` only for a team the user belongs to. Omit it for the personal workspace.

`shorten_link` is limited to 100 creates per minute per token. A flagged destination comes back as `BLOCKED_URL`. Do not retry that URL.

## Find and edit

- `list_links` browses a workspace. `search_links` needs at least one of `slug`, `target`, `tag`, or `query`. There is no tag list. `tag` filters the title.
- `update_link` changes only the fields the user named. Send the link id from a list or search result.

## Delete

`delete_link` permanently removes the short link, its click history, and its pixel attachments. The short URL stops working. Repeat the link id and destination back to the user and wait for an explicit yes before calling it.
