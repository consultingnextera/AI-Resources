# Agent System Audit

A research prompt you fill out and send to multiple LLMs — Grok, Gemini, ChatGPT, Claude — to get design perspectives on your autonomous agent setup. Different models will surface different blind spots. Compare their responses to find what's worth acting on.

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you about your system and fill out the template below, ready to send to other LLMs
- **Copy just the template** — scroll to the bottom, fill in the placeholders yourself, then send it

---

## LLM Instructions

Read this file, then conduct the following interview with me. Ask one group at a time and wait for my answers. When I've answered everything, fill out the template at the bottom of this file using my exact details — not generic descriptions. The filled template is what I'll send to other LLMs for architecture review.

**GROUP 1 — Your System**
1. What is your agent system called and what does it run on? (VPS, local machine, cloud VM, etc.)
2. Is it 24/7 autonomous or on-demand?
3. What AI runtime or framework does it use, and what version?
4. How is it exposed and how do you access it? (loopback, Tailscale, public, etc.)

**GROUP 2 — Orchestration**
5. What does your orchestrator do — how does it route tasks?
6. What does it never do directly?
7. What model does it use and why?

**GROUP 3 — Agents**
8. How many specialist agents do you have? List each one with its role and the model it uses.

**GROUP 4 — Memory**
9. What is your primary memory store?
10. Do you have a secondary store?
11. Any memory quality rules — trust scoring, TTLs, compaction thresholds?

**GROUP 5 — Automation**
12. Do you have a heartbeat or pulse? How often and what does it do?
13. Any nightly or scheduled jobs?
14. What cron jobs are running?
15. Any weekly jobs?

**GROUP 6 — Learning Loops**
16. What learning loops have you defined or implemented?

**GROUP 7 — Security**
17. How is access controlled?
18. How are secrets handled?
19. What's your hard gate mechanism if any?
20. What are your autonomy boundaries — what can the system do without asking vs. what requires approval?

**GROUP 8 — Infrastructure**
21. Describe your infrastructure setup.
22. Do you have a dashboard?
23. How do you sync between machines?
24. What model routing layer do you use?

**GROUP 9 — Assessment**
25. What's working well — what parts are you confident in?
26. Where are the gaps — be specific?
27. What context should the reviewing LLM know about you? (technical level, constraints, preferences)

---

## Template

Copy the block below, fill in every `[PLACEHOLDER]`, then send it to multiple LLMs and compare their responses.

````markdown
---
title: "Research Prompt — Ideal Autonomous Personal Agent System"
version: "1.0"
---

# Research Prompt — Ideal Autonomous Personal Agent System

> **Instructions for the LLM receiving this prompt:** You are acting as a senior systems architect specializing in autonomous AI agent infrastructure. I'm going to describe my current setup, what it does well, and where I think the gaps are. I want you to design what the *best possible version* of this system looks like in [CURRENT MONTH + YEAR] — not theoretical, but buildable with tools that exist today. Be opinionated. Pick sides. Tell me what to keep, what to kill, and what to add.

---

## My Current System

I run a [24/7 autonomous / on-demand] personal AI system called **[YOUR SYSTEM NAME]** on [YOUR INFRASTRUCTURE]. Here's the architecture:

### Runtime
- **[YOUR AI RUNTIME/FRAMEWORK]** (v[VERSION]) — [one-line description]
- Installed via [install method]
- [How it's exposed — e.g. gateway on loopback port XXXX]
- [How you access it — e.g. Tailscale, SSH tunnel, direct]

### Orchestration
- **[YOUR ORCHESTRATOR NAME]** routes all tasks to specialist agents using [your pattern — e.g. hub-and-spoke, event-driven]
- [What it does and doesn't do]
- Model: [MODEL NAME] — [why you chose it]

### Specialist Agents ([N] total)

| Agent | Role | Model |
|-------|------|-------|
| [NAME] | [ROLE] | [MODEL] |
| [NAME] | [ROLE] | [MODEL] |
| *(add rows as needed)* | | |

### Memory & Persistence
- **[PRIMARY MEMORY STORE]**: [description]
- **[SECONDARY STORE if any]**: [description]
- [Memory quality rules — trust scoring, TTLs, compaction thresholds]

### Automation
- **[HEARTBEAT/PULSE]**: [frequency and what it does]
- **[NIGHTLY JOB]**: [description]
- **Cron jobs**: [list with times]
- **[WEEKLY JOB if any]**: [description]

### Learning Loops ([N] defined)
[List your learning loop types]

### Security Model
- [Access method]
- [Auth method]
- [Secrets handling]
- [Hard gate mechanism if any]
- [Autonomy boundaries]

### Infrastructure
- [VPS/cloud/local setup]
- [Dashboard if any]
- [Version control / sync setup]
- [Model routing layer]

---

## What Works Well
1. [WHAT WORKS #1]
2. [WHAT WORKS #2]
3. [WHAT WORKS #3]

## Where I Think the Gaps Are
1. [GAP #1]
2. [GAP #2]
3. [GAP #3]
4. [GAP #4]
5. [GAP #5]

---

## What I Want You to Design

Design the ideal autonomous personal agent system for [DESCRIBE YOUR CONTEXT]. The system should:

1. **Run [WHERE] with [COST CONSTRAINT]**
2. **Autonomously handle**: [LIST TARGET CAPABILITIES]
3. **React to real-time events** — not just cron schedules
4. **Self-improve measurably** — learning loops that actually execute
5. **Respect hard boundaries** — [YOUR NON-NEGOTIABLES]
6. **Scale gracefully** — adding a new capability shouldn't require restructuring

### Specifically, I want your take on:

**A. Architecture** — Is [YOUR CURRENT PATTERN] still the right orchestration model? Should I move to a different pattern (DAG-based, event-driven, hierarchical, mesh)? What's the tradeoff?

**B. Memory** — Should I stay with [YOUR CURRENT MEMORY APPROACH], move to a vector DB (ChromaDB, Qdrant), or hybrid? How should retrieval work at scale?

**C. Automation triggers** — What should drive agent activity beyond cron? What's the simplest path to event-driven behavior on [YOUR INFRASTRUCTURE]?

**D. Self-improvement** — Of my [N] learning loops, which are actually valuable? What should the self-improvement cycle look like in practice?

**E. External integrations** — What's the minimum set of integrations that would unlock the most autonomous value for [YOUR CONTEXT]?

**F. Agent design** — Are [N] specialists the right number? Should agents be more granular or more general?

**G. Cost optimization** — How should I think about model selection per task? When does local inference make sense vs. API calls?

**H. Filesystem & vault structure** — Is my current folder structure ([YOUR TOP-LEVEL FOLDERS]) optimal? What would you change?

**I. Observability** — How should I monitor agent performance, task completion rates, memory quality, and system health?

**J. The one thing I'm not seeing** — What's the biggest blind spot in my current architecture?

---

## Constraints
- [YOUR TECHNICAL LEVEL]
- [MAINTENANCE REQUIREMENT]
- [RUNTIME CONSTRAINT if any]
- Privacy and security are non-negotiable — no data leaves the system without explicit approval
- [PREFERENCE — e.g. prefer open-source and self-hosted over SaaS]

---

## Output Format

Structure your response as:

1. **Executive Summary** (3-5 sentences — what's the single most important upgrade?)
2. **Architecture Recommendation** (with diagram description if helpful)
3. **Answers to A through J** (be specific — name tools, models, patterns, not just concepts)
4. **Prioritized Upgrade Roadmap** (what to do first, second, third — with estimated effort and impact)
5. **What to Kill** (things in the current system that are dead weight or creating false confidence)
6. **The Non-Obvious Insight** (one thing most people building these systems get wrong that I should avoid)
````

---

> **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
