# linked.is for Cursor

[linked.is](https://linked.is) is a link platform for branded short links, link-in-bio pages, QR codes, and click analytics. This repository ([linkedis/cursor-plugin](https://github.com/linkedis/cursor-plugin)) is the Cursor Marketplace plugin. It connects Cursor to the linked.is MCP server at `https://linked.is/mcp`.

With an API token, the agent can create and manage short links, read click analytics, and edit bio-page buttons. The free creator tools work with the token left empty, and they do not need an account.

## Setup

1. Install **linked.is** from the Cursor Marketplace, or load this repository as a local plugin.
2. Open **Plugins → linked.is → Configure**.
3. For account tools, paste an API token from [linked.is Settings → API](https://linked.is/settings/api). The token starts with `lnk_` and is shown once. Cursor stores it as the optional variable `LINKEDIS_API_TOKEN`. This repository does not contain a token.
4. Leave **linked.is API token** empty to use only the free tools.

The plugin sends `Authorization: Bearer ${LINKEDIS_API_TOKEN}`. An empty value is sent as a blank bearer, which the server treats as anonymous.

## Tools

Account tools need `LINKEDIS_API_TOKEN`.

| Tool | Purpose |
| --- | --- |
| `shorten_link` | Create a short link. Optional slug, title, UTM source/medium/campaign, and an active custom domain. |
| `list_links` | Paginated list, with optional slug, destination, and title filters. |
| `search_links` | Search by slug, destination, title, or a general query. |
| `update_link` | Change URL, slug, title, or UTM fields. |
| `delete_link` | Permanently delete a link and its click history. The agent repeats the link and waits for an explicit yes before calling it. |
| `get_link_analytics` | Clicks, countries, referrers, and sources for one link or the workspace. |
| `generate_qr_code` | PNG QR code for a short link you own. |
| `list_bio_pages` | Bio pages and their link buttons. |
| `add_bio_link` | Append a link button. |
| `remove_bio_link` | Permanently remove one link button. The agent repeats the button and waits for an explicit yes before calling it. |
| `reorder_bio_links` | Reorder every link button on a page. |
| `list_domains` | Custom domains and whether each one can serve short links. |

Free tools work with no token:

| Tool | Purpose |
| --- | --- |
| `free_shorten_url` | Anonymous short URL, with no click stats. |
| `free_qr_code` | PNG QR code of any text or URL. |
| `utm_link` | URL with UTM parameters, including term and content. |
| `whatsapp_link` | `https://wa.me` link. |
| `youtube_thumbnail_urls` | YouTube thumbnail image URLs. |
| `youtube_timestamp_link` | YouTube link that starts at a time. |
| `convert_color` | Hex color as RGB, HSL, HSB, contrast, and harmonies. |
| `separate_text` | Split text on one separator and join with another. |
| `remove_duplicate_lines` | Drop duplicate lines, keeping the first. |
| `base64_codec` | Encode or decode text as Base64. |
| `draw_giveaway` | Pick giveaway winners from a list of names. |

## Skills

Skills in `skills/` tell the agent which tool to call, when to confirm a destructive change, and how to summarize analytics.

| Skill | Use |
| --- | --- |
| `manage-short-links` | Create, find, update, and delete short links, including UTM parameters and custom domains. |
| `read-link-analytics` | Read click analytics for one link or a workspace and summarize the numbers that came back. |
| `manage-bio-pages` | List bio pages and add, remove, or reorder their link buttons. |
| `use-free-tools` | Free creator tools that work without an API token. |

## Layout

```text
├── .cursor-plugin/plugin.json
├── mcp.json
├── assets/logo.svg
├── skills/
├── scripts/validate-cursor-plugin.mjs
├── LICENSE
└── README.md
```

This is a single-plugin repository. `.cursor-plugin/plugin.json` is at the root, so no `marketplace.json` is required.

Check the plugin from the repository root:

```bash
node scripts/validate-cursor-plugin.mjs
```

## License

[MIT](LICENSE)
