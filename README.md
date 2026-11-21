# Lumina Tasks MCP server

Remote MCP server for [Lumina](https://lumina-app.me), a tasks, habits, notes and focus app. "Lumina Tasks" is the name Lumina uses in directories: same app, same account, same server. It lets an AI assistant (Claude, ChatGPT, or any MCP client) save what you talk about straight into your Lumina.

**Server URL:** `https://lumina-app.me/mcp`

- Transport: Streamable HTTP
- Auth: OAuth 2.1 with PKCE and dynamic client registration. Metadata is at `https://lumina-app.me/.well-known/oauth-protected-resource`.
- You need a free Lumina account with sync turned on. You approve each assistant in the app and can disconnect it at any time.

## Tools

| Tool | What it does | Scope |
|---|---|---|
| `list_today` | List the day's tasks (with their steps) and habits | `tasks.read` |
| `search` | Search tasks (title, notes or steps), habits and notes | `tasks.read` |
| `get_task` | Read one task: notes, date, time, priority, repeat, reminder and its steps | `tasks.read` |
| `add_task` | Add a task, with an optional date, time, repeat, priority and steps | `tasks.write` |
| `add_subtasks` | Add steps to an existing task | `tasks.write` |
| `complete_task` | Check or uncheck a task (its steps follow, as in the app) | `tasks.write` |
| `complete_subtask` | Check or uncheck a step (the task is checked when all its steps are) | `tasks.write` |
| `update_task` | Change a task's title, notes, date, time, priority, repeat or reminder | `tasks.edit` |
| `rename_subtask` | Rename a step | `tasks.edit` |
| `delete_task` | Delete a task and its steps | `tasks.edit` |
| `delete_subtask` | Delete a step | `tasks.edit` |
| `add_habit` | Add a habit on chosen weekdays | `habits.write` |
| `add_note` | Add a note | `notes.write` |
| `add_event` | Add an event to the linked Google Calendar | `calendar.write` |
| `add_to_group` | Add a task to a shared group (editor role) | `groups.write` |

Priority goes from 0 (none) to 3 (high); the app shows it as 1 to 3 colored icons. Changes and deletions (`tasks.edit`) apply right away; an assistant connected before this permission existed must be reconnected to get it.

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
