# Lumina Tasks MCP server

Remote MCP server for [Lumina Tasks](https://lumina-app.me), a tasks, habits, notes and focus app. It lets an AI assistant (Claude, ChatGPT, or any MCP client) save what you talk about straight into your Lumina.

**Server URL:** `https://lumina-app.me/mcp`

- Transport: Streamable HTTP
- Auth: OAuth 2.1 with PKCE and dynamic client registration. Metadata is at `https://lumina-app.me/.well-known/oauth-protected-resource`.
- You need a free Lumina account with sync turned on. You approve each assistant in the app and can disconnect it at any time.

## Tools

| Tool | What it does | Scope |
|---|---|---|
| `add_task` | Add a task, with an optional date, time, repeat and priority | `tasks.write` |
| `add_habit` | Add a habit on chosen weekdays | `habits.write` |
| `add_note` | Add a note | `notes.write` |
| `add_event` | Add an event to the linked Google Calendar | `calendar.write` |
| `list_today` | List today's tasks and habits | `tasks.read` |
| `complete_task` | Mark a task done | `tasks.write` |
| `search` | Search tasks, habits and notes | `tasks.read` |
| `add_to_group` | Add a task to a shared group (editor role) | `groups.write` |

Everything an assistant adds shows the assistant's name and waits in the app's AI inbox until you keep it, unless you turn on "Validate automatically".

## Connect

- **Claude:** Settings → Connectors → Add custom connector → paste `https://lumina-app.me/mcp`.
- **ChatGPT:** Settings → Connectors (developer mode) → add `https://lumina-app.me/mcp`.
- **Other clients:** add a remote server with the URL above. The client registers itself and opens the Lumina approval screen.

The full guide is available in 6 languages: [English](https://lumina-app.me/en/ai), [Français](https://lumina-app.me/ia), [Deutsch](https://lumina-app.me/de/ki), [Español](https://lumina-app.me/es/ia), [Italiano](https://lumina-app.me/it/ia), [Português](https://lumina-app.me/pt/ia).

## Privacy

- No ads, no trackers.
- Lumina does not sell your data and uses none of it to train AI models.
- What an assistant reads or writes is also processed by that assistant's provider, under its own terms.
- See the [privacy policy](https://lumina-app.me/privacy).

This repository only describes the hosted server, for MCP directories. Lumina's source code is not public.
