# alephlo — worldwide classifieds for AI assistants (MCP)

Worldwide classifieds you use by asking your assistant: find and post have / need listings (goods, jobs, services, homes, cars) and message owners. Free, no ads, no paid ranking.

[alephlo](https://alephlo.com) is a "have / need" board in 1,100+ categories and 25 site languages. These are its two remote MCP servers — hosted by alephlo, nothing to install, no API key.

| Server | URL | Sign-in | Tools |
|---|---|---|---|
| Your own connection | `https://alephlo.com/mcp/me` | OAuth 2.1 — your email and a one-time code, no password | all 18 below |
| Search only | `https://alephlo.com/mcp` | none | `search_listings`, `get_listing`, `list_listing_categories` (read-only) |

Transport: streamable HTTP. MCP Registry names: `com.alephlo/classifieds` (`/mcp/me`, the [server.json](server.json) here) and `com.alephlo/search` (`/mcp`).

## Connect

- **Claude** (claude.ai, Desktop, mobile): Settings → Connectors → Add custom connector → `https://alephlo.com/mcp/me`
- **ChatGPT** (paid plans): turn on developer mode for connectors in Settings and add a custom MCP connector with the same address
- **Claude Code**: `claude mcp add --transport http alephlo https://alephlo.com/mcp/me`
- **Cursor** — `~/.cursor/mcp.json`:
  ```json
  { "mcpServers": { "alephlo": { "url": "https://alephlo.com/mcp/me" } } }
  ```
- **VS Code** — `.vscode/mcp.json`:
  ```json
  { "servers": { "alephlo": { "type": "http", "url": "https://alephlo.com/mcp/me" } } }
  ```
- **Any other MCP client** with streamable HTTP and OAuth. Only searching? Use `https://alephlo.com/mcp` — no sign-in at all.

The first call that needs you opens alephlo's own sign-in page: type your email there, then the 6-digit code alephlo sends. Never paste the code into a chat.

## Tools

| Tool | What it does |
|---|---|
| `search_listings` | Search listings anywhere — nearest first when you give a city (in any language); price filters compare currencies at the day's rate |
| `get_listing` | One listing with all its photos and the owner's counted facts |
| `list_listing_categories` | Categories and each section's fields |
| `post_listing` | Post a "have" or "need" listing — checked before it appears |
| `add_photo` | Add a photo you gave in the chat (or by a link) to your listing |
| `my_listings` | Your listings and their status |
| `edit_listing` | Change your listing |
| `close_listing` | Close your listing |
| `renew_listing` | Put your listing back on the board for another month |
| `send_message` | Write to a listing's owner — your email is not shown |
| `my_messages` | Read your conversations and replies |
| `report_listing` | Report a listing that breaks the rules |
| `report_message` | Report a message you received |
| `create_alert` | Save a search — alephlo emails you when a fitting listing appears |
| `my_alerts` | Your saved searches |
| `delete_alert` | Delete a saved search |
| `set_notifications` | Turn your email notifications off, or on with your clear agreement |
| `withdraw_consent` | Disconnect alephlo from your assistant |

## Examples

1. *"I'm in Lisbon and need a used road bike under 300 euros — what's on alephlo?"* — the assistant searches near Lisbon, nearest first; if nothing fits yet, it saves an alert.
2. *"Post a listing for me: I'm selling my 2019 MacBook Air in Berlin, 550 euros, good condition."* — it picks the category, fills its fields and posts; the listing is checked before it shows, usually within minutes.
3. *"Did anyone write about my bike? Tell the first one I can meet on Saturday."* — it reads your messages and replies to the right one. Later: *"I sold it — close the listing."*

## Rules and privacy

Listings may not contain phone numbers, email addresses or links; every listing and photo is checked before it appears. People contact each other through alephlo. A live listing is public. No ads, no paid ranking, no payments inside alephlo.

[Rules](https://alephlo.com/rules) · [Privacy](https://alephlo.com/privacy) · [About](https://alephlo.com/about)

## Without MCP

- Guide for AI assistants: [llms.txt](https://alephlo.com/llms.txt)
- JSON: `https://alephlo.com/api/v1/listings?q=bicycle&city=Munich&country=DE`
- Server cards: [/mcp/server-card](https://alephlo.com/mcp/server-card) · [/mcp/me/server-card](https://alephlo.com/mcp/me/server-card) · [ai-catalog.json](https://alephlo.com/.well-known/ai-catalog.json)

## This repository

It holds no server code — the servers above run on alephlo.com. It describes them for MCP directories and clients. Questions: privacy@alephlo.com or an issue here.

License: MIT (this text and the configuration examples).
