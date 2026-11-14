---
name: use-free-tools
description: Use the linked.is free creator tools that work without an API token. Use for WhatsApp links, UTM URLs, YouTube helpers, color conversion, text cleanup, Base64, giveaways, anonymous short links, and QR codes.
---

# Free creator tools

These linked.is MCP tools work when `LINKEDIS_API_TOKEN` is empty. They do not read or change an account. Prefer the account tools in the other skills when a token is set and the user wants to own the result.

| Need | Tool |
| --- | --- |
| Anonymous short URL, no stats, 5 per minute per IP | `free_shorten_url` |
| PNG QR of any text or URL | `free_qr_code` |
| URL with UTM parameters, including term and content | `utm_link` |
| `https://wa.me` link | `whatsapp_link` |
| YouTube thumbnail image URLs | `youtube_thumbnail_urls` |
| YouTube link that starts at a time | `youtube_timestamp_link` |
| Hex color as RGB, HSL, HSB, contrast, and harmonies | `convert_color` |
| Split text on one separator and join with another | `separate_text` |
| Drop duplicate lines, keeping the first | `remove_duplicate_lines` |
| Encode or decode text as Base64 | `base64_codec` |
| Pick giveaway winners from a list of names | `draw_giveaway` |

Do not use these tools for work that belongs on an account. A short link the user wants to edit, track, or put on their domain is `shorten_link`. A QR for a short link they own is `generate_qr_code`.

The visual QR designer, picking a color from a picture or the screen, and the giveaway certificate are not tools. Return the text or image these tools already produce.
