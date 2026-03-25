# AI-Resources

A collection of prompts, system files, skills, and n8n workflows for founders and operators building with AI. Everything here is practical — no theory, no fluff. Paste a file, answer some questions, get something useful out.

Built and maintained by [Nextera Consulting](https://nexteraconsult.com/ai).

---

## What's in Here

### Prompts/

Ten prompts that work as LLM interviews. Paste any file into Claude, ChatGPT, or Grok — it will ask you the right questions and fill out the template at the bottom. Or skip the interview and copy the template directly.

| File | What It Produces |
|---|---|
| `MD Files/BUSINESS.md` | A persistent business context file any AI tool can load |
| `MD Files/USER.md` | A user profile so agents understand who you are and how you work |
| `MD Files/VOICE_PROFILE.md` | A voice style guide so AI writes in your tone, not generic AI |
| `MD Files/MEMORY.md` | Seed memory entries for an AI agent system |
| `MD Files/SOUL.md` | Character and values file for an AI orchestrator |
| `Rules Generator.md` | A rules file (`cursor.rules` / `windsurf.rules` / `CLAUDE.md`) for your AI coding tool |
| `Automation Opportunity Finder.md` | A prioritized automation opportunities report for your business |
| `n8n workflow designer.md` | A complete n8n workflow blueprint from a plain English process description |
| `Openclaw Setup.md` | Step-by-step guide to building a 24/7 autonomous agent system with OpenClaw |
| `Openclaw audit and upgrade.md` | A filled research prompt to send to multiple LLMs for architecture review |

Start with `MD Files/BUSINESS.md` and `MD Files/USER.md` — these two files make every AI interaction significantly more useful. The `MD Files/` prompts produce vault-ready context files. The rest are tools you'll use repeatedly.

---

### Skills/

Drop-in skill files for Claude's skill system. Load them once and Claude follows the methodology automatically.

| File | What It Does |
|---|---|
| `Frontend-design-SKILL.md` | 10-step process for building production-grade frontend interfaces — brief-faithful, responsive, never generic |
| `Vibe-code-SKILL.md` | YC vibe coding methodology for AI-assisted development — planning, version control, debugging, tool optimization |

---

### n8n Workflows/

Ready-to-import n8n workflows that connect external services to an AI agent system. Each workflow polls a service on a schedule and writes structured event files that your agent system can consume.

| File | What It Does |
|---|---|
| `Email Inbox to Agent.json` | Polls Gmail for unread emails every 5 minutes |
| `Calendar to Agent.json` | Polls Google Calendar for upcoming events every 15 minutes |
| `CRM to Agent.json` | Polls HubSpot contacts and deals every 10 minutes |
| `X to Agent.json` | Polls X (Twitter) mentions and DMs every 15 minutes |

See `n8n Workflows/README.md` for setup instructions, event file format, and customization guide.

---

## How to Use This Repo

**Starting from scratch with AI tools:**
Start with `MD Files/BUSINESS.md` and `MD Files/USER.md`. These two files, once filled out, make every AI interaction significantly more useful.

**Building an agentic system:**
Work through the `MD Files/` prompts to generate your context files, then follow `Openclaw Setup.md` to stand up the system. Use `Openclaw audit and upgrade.md` to get architecture feedback from multiple LLMs before you build.

**Automating a specific process:**
Use `Automation Opportunity Finder.md` to find your highest-value automation opportunities, then `n8n workflow designer.md` to design the workflow. Import the matching JSON from `n8n Workflows/` if one exists for your service.

**AI-assisted coding:**
Install `Vibe-code-SKILL.md` in Claude, then use `Rules Generator.md` to generate a rules file for your project.

---

## License

MIT — use it however you want. See `LICENSE` for details.

Third-party repositories and tools referenced here are subject to their own licenses.

---

> Questions or want this built for you — **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
