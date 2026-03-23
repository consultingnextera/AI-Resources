---
title: "Research Prompt Template — Ideal Autonomous Personal Agent System"
version: "1.0"
purpose: >
  Send to multiple LLMs (Grok, Gemini, ChatGPT, Claude, etc.) to gather design
  perspectives on your autonomous agent setup. Fill in every [PLACEHOLDER] with
  your own system details before sending.
license: MIT
---

<!--
HOW TO USE THIS TEMPLATE
========================
1. Replace every [PLACEHOLDER] with your own system details.
2. Delete any sections that don't apply to your setup.
3. Add sections that reflect capabilities unique to your system.
4. Send the filled-in version to multiple LLMs and compare responses.
5. The questions in sections A–J are the valuable part — keep them as-is.
-->

# Research Prompt — Ideal Autonomous Personal Agent System

> **Instructions for the LLM receiving this prompt:** You are acting as a senior systems architect specializing in autonomous AI agent infrastructure. I'm going to describe my current setup, what it does well, and where I think the gaps are. I want you to design what the *best possible version* of this system looks like in [CURRENT MONTH + YEAR] — not theoretical, but buildable with tools that exist today. Be opinionated. Pick sides. Tell me what to keep, what to kill, and what to add.

---

## My Current System

I run a [24/7 autonomous / on-demand] personal AI system called **[YOUR SYSTEM NAME]** on [YOUR INFRASTRUCTURE — e.g. a VPS, a local machine, a cloud VM]. Here's the architecture:

### Runtime
- **[YOUR AI RUNTIME/FRAMEWORK]** (v[VERSION]) — [one-line description of what it does]
- Installed via [install method — e.g. npx, pip, docker]
- [How it's exposed — e.g. gateway on loopback port XXXX, public API, local only]
- [How you access it — e.g. Tailscale, SSH tunnel, direct]

### Orchestration
- **[YOUR ORCHESTRATOR NAME]** routes all tasks to specialist agents using [your pattern — e.g. hub-and-spoke, DAG, event-driven]
- [Describe what the orchestrator does and doesn't do — e.g. "never does specialist work, only classifies and delegates"]
- Model: [MODEL NAME] — [why you chose it, e.g. cheap/fast for routing]

### Specialist Agents ([N] total)
<!--
List your agents. If you don't have named agents, describe your tool/function setup instead.
-->

| Agent | Role | Model |
|-------|------|-------|
| [NAME] | [ROLE] | [MODEL] |
| [NAME] | [ROLE] | [MODEL] |
| [NAME] | [ROLE] | [MODEL] |
| *(add rows as needed)* | | |

### Memory & Persistence
- **[PRIMARY MEMORY STORE]**: [description — e.g. markdown files in a git-versioned folder, SQLite, vector DB]
- **[SECONDARY STORE if any]**: [description — e.g. Supabase/PostgreSQL for structured data]
- [Any memory quality rules — e.g. trust scoring, TTLs, compaction thresholds]

### Automation
- **[HEARTBEAT/PULSE]**: [frequency and what it does — e.g. 6-hour sync: git sync, memory watchdog, task audit]
- **[NIGHTLY/SCHEDULED JOB]**: [description — e.g. 03:00 nightly audit: maintenance, inbox, security scan]
- **Cron jobs**: [list with times — e.g. backup at 02:00, digest at 04:00, memory index 4x daily]
- **[WEEKLY JOB if any]**: [description]

### Learning Loops ([N] defined)
[List your learning loop types — e.g. regression tracking, prediction logging, nightly extraction, friction detection, trust scoring, self-review, etc.]

### Security Model
- [Access method — e.g. Tailscale ZTNA / no public ports, VPN, public with auth]
- [Auth method — e.g. pubkey SSH only, API key, OAuth]
- [Secrets handling — e.g. secrets.env only, never in git]
- [Hard gate mechanism if any — e.g. security agent must approve all code/deploy changes]
- [Autonomy boundaries — e.g. what the system can do without asking vs. what requires approval]

### Infrastructure
- [VPS/cloud/local setup]
- [Dashboard if any — e.g. Next.js dashboard at your-domain.com]
- [Version control setup — e.g. Mac ↔ VPS sync via git]
- [Model routing layer if any — e.g. OpenRouter, LiteLLM, direct API calls]

---

## What Works Well
<!--
Be honest. What parts of your system are you confident in?
-->
1. [WHAT WORKS #1]
2. [WHAT WORKS #2]
3. [WHAT WORKS #3]
4. *(add as needed)*

## Where I Think the Gaps Are
<!--
Be specific. Vague gaps get vague answers.
-->
1. [GAP #1 — e.g. task autonomy is limited, system monitors but rarely initiates]
2. [GAP #2 — e.g. everything is cron-based, no real-time event triggers]
3. [GAP #3 — e.g. memory retrieval is brute-force, no semantic search]
4. [GAP #4 — e.g. self-improvement loops are defined but not running]
5. [GAP #5 — e.g. no external integrations beyond web search]
6. *(add as needed)*

---

## What I Want You to Design

Design the ideal autonomous personal agent system for [DESCRIBE YOUR CONTEXT — e.g. a solo founder running a consulting business / a developer managing personal projects / a researcher synthesizing information]. The system should:

1. **Run [WHERE] with [COST CONSTRAINT — e.g. < $100/month infrastructure, < $200/month API spend]**
2. **Autonomously handle**: [LIST YOUR TARGET CAPABILITIES — e.g. task management, content pipeline, research, system maintenance, security monitoring]
3. **React to real-time events** — not just cron schedules
4. **Self-improve measurably** — learning loops that actually execute
5. **Respect hard boundaries** — [YOUR NON-NEGOTIABLES — e.g. never spend money, publish content, or send messages without approval]
6. **Scale gracefully** — adding a new capability shouldn't require restructuring

### Specifically, I want your take on:

**A. Architecture** — Is [YOUR CURRENT PATTERN — e.g. hub-and-spoke] still the right orchestration model? Should I move to a different pattern (DAG-based, event-driven, hierarchical, mesh)? What's the tradeoff?

**B. Memory** — Should I stay with [YOUR CURRENT MEMORY APPROACH], move to a vector DB (ChromaDB, Qdrant), or hybrid? How should retrieval work at scale? What about episodic vs semantic vs procedural memory separation?

**C. Automation triggers** — What should drive agent activity beyond cron? Webhooks? File watchers? Message queues? What's the simplest path to event-driven behavior on [YOUR INFRASTRUCTURE]?

**D. Self-improvement** — Of my [N] learning loops, which are actually valuable? What should the self-improvement cycle look like in practice (not theory)?

**E. External integrations** — What's the minimum set of integrations that would unlock the most autonomous value for [YOUR CONTEXT — e.g. a consultant, a developer, a researcher]? (Email, calendar, Slack, financial data, CRM, etc.)

**F. Agent design** — Are [N] specialists the right number? Too many? Too few? Should agents be more granular or more general? Should I use tool-calling agents instead of role-based agents?

**G. Cost optimization** — How should I think about model selection per task? When does local inference (Ollama) make sense vs. API calls? How do I track and optimize API spend?

**H. Filesystem & vault structure** — Is my current folder structure ([LIST YOUR TOP-LEVEL FOLDERS — e.g. memory/, loops/, agents/, tasks/, scripts/, src/]) optimal? What would you change?

**I. Observability** — How should I monitor agent performance, task completion rates, memory quality, and system health? Dashboard? Logs? Alerts?

**J. The one thing I'm not seeing** — What's the biggest blind spot in my current architecture? What would a world-class system have that mine doesn't?

---

## Constraints
- [YOUR TECHNICAL LEVEL — e.g. non-technical founder who can read code and run commands but doesn't write from scratch / experienced developer / sysadmin]
- [MAINTENANCE REQUIREMENT — e.g. must be maintainable by AI agents themselves / maintained manually / small team]
- [RUNTIME CONSTRAINT if any — e.g. using OpenClaw as runtime, suggestions should work within it or clearly state if they require replacing it]
- Privacy and security are non-negotiable — no data leaves the system without explicit approval
- [PREFERENCE — e.g. prefer open-source and self-hosted over SaaS where feasible]

---

## Output Format

Structure your response as:

1. **Executive Summary** (3-5 sentences — what's the single most important upgrade?)
2. **Architecture Recommendation** (with diagram description if helpful)
3. **Answers to A through J** (be specific — name tools, models, patterns, not just concepts)
4. **Prioritized Upgrade Roadmap** (what to do first, second, third — with estimated effort and impact)
5. **What to Kill** (things in the current system that are dead weight or creating false confidence)
6. **The Non-Obvious Insight** (one thing most people building these systems get wrong that I should avoid)
