# n8n → Event-Driven Agent Workflows

Drop-in n8n workflows that poll external services and write structured event files for AI agent systems to consume. Built for solo founders running autonomous agent architectures.

## What This Does

Instead of building custom API integrations for every service, these workflows follow one pattern:

```
External Service → n8n (scheduled poll) → Event File (.md with YAML frontmatter) → Your Agent System
```

Your agent system watches a directory for new `.md` files. When one appears, it reads the YAML frontmatter to understand the event type and priority, then routes it to the right handler.

## Workflows Included

### Event Intake — External Services → Agent

| Workflow | File | What It Polls | Event Type |
|----------|------|---------------|------------|
| Gmail Inbox | `Email Inbox to Agent.json` | Unread emails | `email_received` |
| Google Calendar | `Calendar to Agent.json` | Upcoming events (24h) | `calendar_reminder` |
| HubSpot CRM | `CRM to Agent.json` | Recent contacts + deals | `crm_update` |
| X (Twitter) | `X to Agent.json` | Mentions + DMs | `social_mention` |

### Content Pipeline — Agent → Discord → Supabase

| Workflow | File | What It Does | Trigger |
|----------|------|--------------|---------|
| Content Notify to Discord | `Content Notify to Discord.json` | Polls Supabase for new content drafts and posts them to a Discord channel for review | Every 30 min |
| Content Approve/Revise/Kill | `Content Approve Revise Kill.json` | Listens for Discord replies (`approve`, `revise: [notes]`, `kill`) and updates content status in Supabase | Discord message |

## Quick Start

1. **Import** — In n8n, go to Settings → Import from File for each JSON
2. **Credentials** — Replace `REPLACE_WITH_CREDENTIAL_ID` with your n8n credential IDs and connect your OAuth/bot accounts
3. **Configure paths** — Search and replace `/path/to/your/events/` with your actual events directory path
4. **Activate** — Turn on each workflow

## Event File Format

Every event intake workflow writes files in this format:

```yaml
---
type: email_received
source: n8n
priority: normal
timestamp: 2026-03-24T15:00:00.000Z
processed: false
gmail_message_id: abc123
---
# Email: Meeting Follow-up

**From**: jane@example.com
**Subject**: Q2 Planning

## Body Preview

Let's schedule time to discuss...

## Action Needed

Route to the appropriate handler based on content type.
```

The `type` and `priority` fields let your agent system make routing decisions without parsing the full body.

## Content Pipeline — How It Works

The two content workflows work together as a Discord-based approval loop:

```
Agent generates content draft → saved to Supabase
    ↓
Content Notify polls Supabase every 30 min → posts draft to Discord #content channel
    ↓
You reply in Discord: approve | revise: [notes] | kill
    ↓
Content Approve reads your reply → updates status in Supabase
    ↓
If revised: writes event file to trigger agent regeneration
```

**Discord commands:**
- `approve` — marks draft as ready to publish
- `revise: your notes here` — marks as revision requested and fires an event to regenerate
- `kill` — archives the draft

**Supabase table required:** `content_packages` with columns: `id`, `idea_id`, `platform`, `post_copy`, `hook_options`, `image_prompt`, `status`, `notified_at`, `discord_message_id`, `revision_notes`, `created_at`, `updated_at`

**Environment variables required:**
- `DISCORD_CONTENT_CHANNEL_ID` — the Discord channel ID where drafts get posted

## Security

Event intake workflows sanitize all user-controlled content before writing:
- Newlines in subjects/names are stripped (prevents YAML frontmatter injection)
- YAML delimiters (`---`) in content are replaced with em-dashes
- File content is base64-encoded before shell write (prevents shell injection)
- Filenames are restricted to alphanumeric + hyphens only
- Calendar events use a dedupe log to prevent duplicate files

## Customization

**Change poll intervals** — Edit the Schedule Trigger node in each workflow. Defaults: Gmail 5min, Calendar 15min, HubSpot 10min, X 15min, Content Notify 30min.

**Change priority rules** — Each Code node has a priority section. Edit the if/else block to match your needs.

**Add more services** — Copy any event intake workflow as a template. The pattern is always: Schedule Trigger → API Node → Code (transform to YAML) → Execute Command (write to file).

**Change the events directory** — Find/replace `/path/to/your/events/` with your path in all JSON files.

## Requirements

- n8n (self-hosted or cloud)
- A directory your agent system watches for new `.md` files (event intake workflows)
- OAuth credentials for whichever services you want to connect
- Discord bot token + Supabase PostgreSQL connection (content pipeline workflows)

## File Watcher

The event intake workflows don't include the watcher — that's part of your agent system. A minimal inotify-based watcher:

```bash
#!/bin/bash
EVENTS_DIR="/path/to/events"
inotifywait -m -e create --format '%f' "$EVENTS_DIR" | while read FILE; do
  if [[ "$FILE" == *.md ]]; then
    # Your agent routing logic here
    echo "New event: $FILE"
    mv "$EVENTS_DIR/$FILE" "$EVENTS_DIR/processed/"
  fi
done
```

## License

MIT — use it however you want.
