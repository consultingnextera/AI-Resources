# How to Set Up Your Own Autonomous AI Agent System with OpenClaw

## What This Is

Most people use AI reactively — open a chat, ask a question, close it. Every session starts from zero. The AI has no memory of your business, your clients, your preferences, or what you figured out last week.

This guide shows you how to build the opposite: a persistent, event-driven autonomous agent system that runs 24/7, learns from its own mistakes, and handles real work — research, content, email, CRM updates, system monitoring — without you having to babysit it.

The runtime is **OpenClaw**, an open-source multi-agent framework. The architecture is battle-tested: a single VPS, 8 specialist AI agents orchestrated by a central router, a hybrid memory system, and n8n workflows that pipe real-world events (email, calendar, CRM) into the system automatically.

This is not a beginner chatbot setup. It's a working autonomous system.

---

## What You're Building

> **This is the v2 event-driven architecture** — not the simpler cron-only setup you'll find in most agent tutorials. The core difference: instead of agents running on a schedule and hoping something changed, external events (emails, calendar invites, CRM updates) actively trigger the system in real time. Cron heartbeats still run every 6 hours as a safety net, but the primary driver is events.

```
External world (email, calendar, CRM, webhooks)
    ↓
n8n catches events → writes .md files to /events/
    ↓
inotify watches /events/ → fires POST to OpenClaw gateway
    ↓
The Orchestrator receives event → routes to specialist agent
    ↓
Specialist executes → writes result to vault or Supabase
    ↓
Event moves to /events/processed/
```

**The 9 specialist agents** (names are yours to customize — these are the roles):

| Role | What They Do |
|---|---|
| Orchestrator | Routes all tasks, enforces permissions, never does specialist work |
| Intake | First responder — classifies every inbound event and routes it |
| Researcher | Web research, source synthesis, fact-cited output |
| Strategist | Planning, roadmaps, trade-off analysis |
| Content Engine | Content pipeline — ideas → briefs → full packages → approval queue |
| Coder | Code writing, debugging, refactoring |
| Monitor | System health, service status, friction scanning |
| Memory Curator | Vault memory, embeddings, knowledge compaction |
| Security Auditor | Hard gate for all code and deploy changes |

**Memory (hybrid):**
- Markdown vault — git-versioned, human-readable, source of truth
- Supabase pgvector — semantic retrieval via 1536-dim embeddings
- Trust scoring on all memory entries (1–10 scale)

**Autonomy (3-tier permission model):**
- Tier 1 (auto): read, research, draft, run loops, git sync — no approval needed
- Tier 2 (implicit): send drafts for review, queue content — auto-executes after 30 minutes unless vetoed
- Tier 3 (hard gate): spend money, publish content, send external messages — explicit approval required

---

## Prerequisites

Before you start, you need:

- **A VPS** — DigitalOcean, Hetzner, or similar. 2GB RAM minimum. Ubuntu 24.04 recommended. ~$12/month.
- **OpenClaw** — Install instructions at docs.openclaw.ai. Current stable: v2026.3.22.
- **n8n (self-hosted)** — The automation layer that pipes external events into the system.
- **OpenRouter account** — Routes your agent API calls to the right models (Gemini, Claude, DeepSeek, etc.) through one API key. Cheaper than direct API access.
- **Supabase account** — Free tier covers the memory/embedding pipeline.
- **Tailscale** — Keeps all services behind a private network. No public ports.
- **Git** — Version control for your vault. Mac ↔ VPS sync.

**Estimated monthly cost:**
- VPS: ~$12
- OpenRouter (all models): ~$30–60
- Supabase: Free tier
- n8n (self-hosted): Free
- Tailscale: Free tier
- **Total: ~$42–72/month**

---

## Step 1 — Install OpenClaw on Your VPS

```bash
# Install Node.js (required)
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs

# Install OpenClaw
npm install -g openclaw@2026.3.22

# Verify
npx openclaw@2026.3.22 doctor
```

Set OpenClaw to run as a systemd service so it restarts automatically:

```bash
# Create service file
sudo nano /etc/systemd/system/openclaw.service

# Add:
[Unit]
Description=OpenClaw Gateway
After=network.target

[Service]
User=YOUR_USERNAME
ExecStart=/usr/bin/npx openclaw@2026.3.22 gateway start
Restart=always
EnvironmentFile=/home/YOUR_USERNAME/PersonalOS/secrets.env

[Install]
WantedBy=multi-user.target

# Enable and start
sudo systemctl enable openclaw
sudo systemctl start openclaw
```

---

## Step 2 — Generate Your Vault

Your vault is the markdown-based workspace OpenClaw reads as its persistent memory and context. Copy the prompt below into any LLM (Claude recommended) and run it. The LLM will generate every file with full content.

Save all output to: `~/PersonalOS/`

---

```
You are an expert at building OpenClaw-compatible autonomous agent vaults.

Generate a complete PersonalOS vault — a markdown-based workspace for an OpenClaw multi-agent system. This vault serves as the persistent memory, context, and operating instructions for a team of 9 AI agents running 24/7 on a VPS.

The vault follows these conventions:
- All root-level directives: SCREAMING_CASE.md
- Agent files in agents/: REGISTRY.md, ORCHESTRATION.md
- Loop files in loops/: SCREAMING_CASE.md
- Memory files in memory/: SCREAMING_CASE.md or snake_case for dated entries
- Every file has YAML frontmatter: title, status (active), domain, updated (YYYY-MM-DD), tags

Generate the following files with full content:

---

ROOT LEVEL (operating directives):

AGENTS.md — Orchestrator operating directive. Include:
- Identity: The Orchestrator is the lead agent. Never does specialist work. Only classifies, delegates, aggregates.
- Boot sequence (files to read in order at session start)
- Delegation pattern: classify → route → pre-read paths → spawn → aggregate
- Orchestration/Persistence protocol: Orchestrator lifecycle = dispatch → aggregate → audit → persist → report. Any report without persistence confirmation is an orchestration failure.
- Autonomy boundaries: Tier 1 (auto), Tier 2 (implicit, 30-min veto window), Tier 3 (hard gate)
- Output rules: all output to markdown files, ISO 8601 timestamps, commit messages [component] description
- Git permissions: auto-commit vault-only changes to main; code/config changes require branch + PR; NEVER commit .env or secrets

SOUL.md — Orchestrator character and values. Include:
- Integrity: never patch regressions twice (architectural audit on repeat failures), atomic ingestion, ghost-free git state before spawning
- Delegation mandate: The Orchestrator is a non-generating router. All synthesis delegated to specialists.
- Core values: lean, private, confirm before external action, no filler
- Networking mandate: all ingress via Tailscale ZTNA, no public ports, SSH pubkey only

IDENTITY.md — Orchestrator name, role, and agent roster. Include all 9 agents (Orchestrator, Intake, Researcher, Strategist, Content, Coder, Monitor, Memory, Security) — use your own names or keep the role labels with triggers, roles, and workspace paths.

USER.md — User profile template. Include sections for: professional background, current projects (production and in-development), daily schedule, revenue streams, communication preferences, and technical communication rules. Populate with placeholder text that prompts the user to fill in their details.

CLAUDE.md — Agent model assignments and OpenClaw commands. Include:
- Agent → model routing table (9 agents)
- Model sync procedure (openclaw.json is source of truth)
- Common OpenClaw commands
- Repo etiquette (commit format, no force-push to main)
- Unexpected behaviors and workarounds (context overflow, hallucinated paths, loop drift, stale memory)

REFERENCE.md — Single navigation index for all vault files. Tables for: core files, loops/, memory/, tasks/, agents/, and vault consistency rules (what to update when something changes).

TOOLS.md — Tech stack reference. Sections for: AI/LLM providers, development and hosting, automation and workflow, communication tools, and database/storage.

HEARTBEAT.md — Automation schedule. Include:
- Sync pulse every 6 hours: git sync, memory watchdog, task audit, DB sync
- Nightly audit at 03:00: memory maintenance, inbox checks, security analysis, project summary
- Cron schedule: backup 02:00, nightly audit 03:00, digest 04:00, memory index 4x daily
- Weekly autonomy improvement on Sundays
- OpenClaw maintenance checklist (dependency audit, environment validation, memory flush, agent health, security check)

INTERACTIONS.md — Proactive clarification patterns. Define when the Orchestrator asks follow-up questions for: memory writes (trust score), research requests (depth), strategy requests (constraints), code requests (production vs prototype), loop triggers (all vs specific), ambiguous output destinations, git operations.

CONCEPTS.md — Shared vocabulary. Define: self-improving agent loop, the 9 learning loops, file-based memory, AGENTS.md standard, PARA method, compound learning, trust score, context engineering.

SECURITY.md — Security policy. Include: API key handling (where keys live, rotation procedure), pre-commit secret detection, secrets runtime protocol, data retention rules.

---

agents/ DIRECTORY:

agents/REGISTRY.md — Master routing table for all 9 specialists. For each agent include: trigger keyword, model (use placeholders like [FAST_MODEL], [STRATEGY_MODEL], [CODE_MODEL] etc.), role, responsibilities, behavior rules, context files, and definition of done. Agents: Researcher, Strategist, Content Engine, Coder, Monitor, Intake, Memory Curator, Security Auditor — use your own names, these are the roles.

agents/ORCHESTRATION.md — Multi-agent workflow. Include: 8-agent routing table with handoff triggers and payloads, handoff protocol (sessions_spawn format), hub-and-spoke topology rules.

---

loops/ DIRECTORY (generate all 9 with YAML frontmatter):

SAFETY_RULES.md — Non-negotiable operating constraints and git workflow rules
GUARDRAILS.md — Failure-to-guardrail pipeline. Starts with 10 template guardrail rules (GR-001 through GR-010). Include active rules table with columns: Rule ID, Rule, Source, Added.
REGRESSIONS.md — Regression tracking. Include entry template with fields: Date, Category, Root Cause, Impact, Lesson, Status, Guardrail.
FRICTIONS.md — Friction detection. Include entry template and friction categories.
PREDICTIONS.md — Prediction logging with calibration dashboard table.
NIGHTLY_EXTRACTION.md — Nightly extraction loop with automation script description.
TRUST_SCORING.md — Trust scoring system. Include scoring criteria table (5 factors with weights), trust formula, threshold table (High/Medium/Low/Untrusted), and decay schedule.
HYPOTHESIS_TESTING.md — Hypothesis testing loop with entry template.
SELF_REVIEW.md — Self-review template for session scoring.
SESSION.md — Session start (boot sequence, 15-step checklist) and session close-out protocol (7-step mandatory housekeeping).
KNOWLEDGE_DISTILLATION.md — Knowledge distillation loop. Include categories: Workflow Best Practices, Technical Patterns, Decision Frameworks, Communication Patterns.
LEARNINGS_WORKFLOW.md — Session-end learnings capture prompt and destinations table.

---

memory/ DIRECTORY:

MEMORY.md — Long-term memory store. Include YAML entry template with required fields: Date, Category, Content, Source, Trust Score, Last Verified, Tags, Status. Include <!-- Append above --> marker at end.
CURRENT_STATE.md — Active system state. Include sections: What's Working (infrastructure and agents), Pending Actions, Active Todos.
TASK_PLAN.md — Current task queue. Include columns: Task ID, Description, Status, Priority, Assignee, Updated.
LEARNINGS.md — Rules extracted from past mistakes. Start with 5 template entries demonstrating the format.
VOICE_PROFILE.md — Your voice style guide. Include sections: core voice attributes, banned phrases list, platform-specific tone, formatting rules (LinkedIn vs email vs internal docs).
SCRATCHPAD.md — Temporary working space, cleared between sessions.

---

tasks/ DIRECTORY:

MASTER_TODO.md — Master active task pipeline. Columns: ID, Task, Priority (1-5), Status, Agent, Strategic Score (impact × urgency), Notes.
PLANNER.md — 30/90/365-day strategic goals. Three sections with placeholder goals.

---

skills/ DIRECTORY:

SKILLS_INDEX.md — Index of all installed skills. Columns: Skill, Purpose, Primary Agent, Added. Include 5 placeholder rows.

---

events/ DIRECTORY:

README.md — How the event system works. Include: event file format (YAML frontmatter fields: type, source, priority, timestamp, processed), event types table (email_received, calendar_reminder, crm_update, social_mention, agent_request), and file lifecycle (new → processed/).

---

FORMAT RULES (apply to every file):
- YAML frontmatter on every file: title, status: active, domain, updated, tags
- Use [[wiki-links]] for all internal file references
- Headings use ## for sections, ### for subsections
- Entry templates use markdown code blocks with filled examples
- Tables use standard markdown pipe syntax
- Append markers (<!-- Append above -->) at the bottom of append-only files
- Never use escaped \n — always actual newlines

Post-generation: list all files generated, confirm all cross-references resolve (every [[link]] points to a real file), and flag any placeholders the user needs to fill in before running OpenClaw.
```

---

## Step 3 — Save the Vault

Create the folder structure and save each generated file:

```bash
mkdir -p ~/PersonalOS/{agents,loops,memory,tasks,skills,events/processed,src,scripts,logs,research,content,archive,sandbox}

# Initialize git
cd ~/PersonalOS
git init
git add .
git commit -m "[init] initial vault setup"
```

---

## Step 4 — Configure OpenClaw

Create `~/.openclaw/openclaw.json` with your agent model assignments.

The config below reflects a battle-tested setup as of March 2026 — fast/cheap models for routing and monitoring, stronger models for strategy, code, and security. Update model strings as newer releases drop; OpenRouter strings always follow the `provider/model-name` format.

```json
{
  "gateway": {
    "bind": "loopback",
    "host": "127.0.0.1",
    "port": 18789,
    "auth": {
      "mode": "token",
      "token": "GENERATE_WITH: npx openclaw@2026.3.22 doctor --generate-gateway-token"
    }
  },
  "agents": {
    "defaults": {
      "workspace": "~/PersonalOS/"
    },
    "list": [
      { "id": "main",     "name": "Orchestrator",       "model": "google/gemini-3.1-flash-lite-preview" },
      { "id": "research", "name": "Researcher",      "model": "minimax/minimax-m2.5" },
      { "id": "strategy", "name": "Strategist",      "model": "anthropic/claude-sonnet-4.6" },
      { "id": "content",  "name": "Content",    "model": "google/gemini-3.1-flash-lite-preview" },
      { "id": "code",     "name": "Coder",    "model": "moonshotai/kimi-k2.5" },
      { "id": "monitor",  "name": "Monitor",  "model": "google/gemini-3.1-flash-lite-preview" },
      { "id": "inbox",    "name": "Intake",      "model": "qwen/qwen3.5-35b-a3b" },
      { "id": "memory",   "name": "Memory",   "model": "google/gemini-3.1-flash-lite-preview" },
      { "id": "security", "name": "Security",        "model": "openai/gpt-5.2-codex" }
    ]
  }
}
```

> **Cost logic**: Gemini Flash Lite handles high-frequency tasks (routing, monitoring, memory) at near-zero cost. Reserve Claude, Kimi, and GPT for tasks where quality matters — strategy, code, and security audits. Use fast/cheap models for research, routing, and memory.

Create `~/PersonalOS/secrets.env` (chmod 600, never commit):

```bash
OPENROUTER_API_KEY=your_key_here
VAULT_PATH=/home/YOUR_USERNAME/PersonalOS
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_anon_key
```

---

## Step 5 — Wire the Event System

The event system is what makes this autonomous rather than just reactive. n8n polls your external services and writes structured `.md` files to `~/PersonalOS/events/`. An inotify watcher catches new files and fires them into OpenClaw.

**Install the event watcher:**

```bash
# Install inotify tools
sudo apt-get install inotify-tools

# Create the watcher script
cat > ~/PersonalOS/scripts/event_watcher.sh << 'EOF'
#!/bin/bash
EVENTS_DIR="$HOME/PersonalOS/events"
GATEWAY="http://127.0.0.1:18789"

inotifywait -m -e create --format '%f' "$EVENTS_DIR" | while read FILE; do
  if [[ "$FILE" == *.md ]]; then
    curl -s -X POST "$GATEWAY/event" \
      -H "Content-Type: application/json" \
      -d "{\"file\": \"$EVENTS_DIR/$FILE\"}"
  fi
done
EOF

chmod +x ~/PersonalOS/scripts/event_watcher.sh
```

**Run it as a systemd service** (same pattern as OpenClaw above).

**Connect n8n workflows:**

This repo includes 4 pre-built n8n workflows in `n8n Workflows/`:
- `Email Inbox to Agent.json` — polls Gmail every 5 minutes
- `Calendar to Agent.json` — polls Google Calendar every 15 minutes
- `CRM to Agent.json` — polls HubSpot contacts and deals every 10 minutes
- `X to Agent.json` — polls mentions and DMs every 15 minutes

Import each into your n8n instance, connect your OAuth credentials, and update the events directory path from `/path/to/your/events/` to `~/PersonalOS/events/`.

---

## Step 6 — Fill In Your Context

These are the files to personalize before your first session:

**`USER.md`** — Replace all placeholder text with your actual background, projects, schedule, and communication preferences. This is what every agent reads to understand who you are.

**`CLAUDE.md`** — Update the model assignments to match whatever models you're actually using via OpenRouter.

**`memory/VOICE_PROFILE.md`** — Fill in your voice and writing style. The Content agent reads this before generating any content.

**`tasks/PLANNER.md`** — Set your 30/90/365-day goals. The Strategist reads this weekly.

**`.env` / `secrets.env`** — Add your API keys.

---

## What to Expect in the First Week

**Day 1:** OpenClaw starts, event watcher runs, the Orchestrator is available via the gateway. You'll get system health reports from the Monitor agent.

**Days 2–3:** Wire up n8n workflows one at a time. Start with calendar (lowest risk), then email, then CRM.

**Days 4–7:** The learning loops start accumulating data. the Memory Curator begins compacting memory. Guardrails start populating as the system catches its own mistakes.

**After week 1:** You'll have a working event-driven system. The self-improvement loops (Failure-to-Guardrail, Preference Distillation, Friction Scanner, Knowledge Distillation) run weekly and compound over time.

---

## Need Help?

Nextera Consulting builds and customizes systems like this end to end — from vault setup and agent configuration to n8n workflow builds and ongoing optimization.

---

> **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
