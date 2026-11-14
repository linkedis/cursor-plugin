---
name: manage-bio-pages
description: List linked.is bio pages and add, remove, or reorder their link buttons. Use when the user wants to change a link-in-bio page.
---

# Manage bio pages

Use the linked.is MCP server. These tools need `LINKEDIS_API_TOKEN`. This skill does not create or delete whole bio pages, and it does not generate bio copy.

## Steps

1. Call `list_bio_pages` before editing. Omit `teamId` for the personal workspace. Each page includes its link buttons with `id`, `label`, `url`, and `order`.
2. `add_bio_link` appends a button. `profileId` is the page id. `label` is the button text. `url` must be http or https.
3. `reorder_bio_links` takes every link button id on that page, in the new order. Headings and other blocks stay in their slots. Do not drop an id.
4. `remove_bio_link` permanently removes one link button. It does not delete the page, and it refuses blocks that are not links. Tell the user the button label and URL and wait for an explicit yes before calling it.
