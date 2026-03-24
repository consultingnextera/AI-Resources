# n8n → Event-Driven Agent Workflows

Drop-in n8n workflows that poll external services and write structured event files for AI agent systems to consume. Built for solo founders running autonomous agent architectures.

## What This Does

Instead of building custom API integrations for every service, these workflows follow one pattern:

```
External Service → n8n (scheduled poll) → Event File (.md with YAML frontmatter) → Your Agent System
```

Your agent system watches a directory for new `.md` files. When one appears, it reads the YAML frontmatter to understand the event type and priority, then routes it to the right handler.

## Workflows Included

| Workflow | File | What It Polls | Event Type |
|----------|------|---------------|------------|
| Gmail Inbox | `gmail-inbox-to-events.json` | Unread emails (IMAP) | `email_received` |
| Google Calendar | `google-calendar-to-events.json` | Upcoming events (24h) | `calendar_reminder` |
| HubSpot CRM | `hubspot-crm-to-events.json` | Recent contacts + deals | `crm_update` |
| X (Twitter) | `x-api-to-events.json` | Mentions + DMs | `social_mention` |

## Quick Start

1. **Import** — In n8n, go to Settings → Import from File for each JSON
2. **Credentials** — Replace `REPLACE_WITH_CREDENTIAL_ID` with your n8n credential IDs and connect your OAuth accounts
3. **Configure paths** — Search and replace `/home/user/PersonalOS/events/` with your actual events directory path
4. **Activate** — Turn on each workflow

## Event File Format

Every workflow writes files in this format:

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

## Security

These workflows sanitize all user-controlled content before writing:

- Newlines in subjects/names are stripped (prevents YAML frontmatter injection)
- YAML delimiters (`---`) in content are replaced with em-dashes
- File content is base64-encoded before shell write (prevents shell injection)
- Filenames are restricted to alphanumeric + hyphens only
- Calendar events use a dedupe log to prevent duplicate files

## Customization

**Change poll intervals** — Edit the Schedule Trigger node in each workflow. Defaults: Gmail 5min, Calendar 15min, HubSpot 10min, X 15min.

**Change priority rules** — Each Code node has a priority section. For example, the Gmail workflow bumps priority for subjects containing "urgent" or "action required". Edit the if/else block to match your needs.

**Add more services** — Copy any workflow as a template. The pattern is always: Schedule Trigger → API Node → Code (transform to YAML) → Execute Command (base64 decode to file).

**Change the events directory** — Find/replace `/home/user/PersonalOS/events/` with your path in all JSON files.

## Requirements

- n8n (self-hosted or cloud)
- A directory your agent system watches for new `.md` files
- OAuth credentials for whichever services you want to connect

## File Watcher

These workflows don't include the watcher — that's part of your agent system. A minimal inotify-based watcher:

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
