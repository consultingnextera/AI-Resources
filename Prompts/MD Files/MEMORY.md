# Agent Memory Setup

The long-term memory store for your AI agent system. Agents write here when they learn something worth keeping — a decision made, a mistake corrected, a preference confirmed. Entries are trust-scored so agents know how much weight to give each one over time.

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and generate your first set of real memory entries using the template below
- **Copy just the template** — scroll to the bottom and start logging entries manually

---

## LLM Instructions

Read this file, then conduct the following interview with me. Ask one group at a time and wait for my answers. When I've answered everything, generate 8-12 completed memory entries using the template at the bottom of this file — ordered by trust score, highest first. These become the starting knowledge base for my agent system.

**GROUP 1 — Preferences**
1. How do you prefer AI outputs to be formatted? (length, structure, tone)
2. What's something AI tools consistently get wrong about how you work?
3. What's a decision you've made about your workflow that you never want to revisit?

**GROUP 2 — Business Rules**
4. What are the 3 most important rules about how you run your business?
5. Are there things you'd never automate or let an agent do without approval?
6. How should agents handle it when something is unclear — ask, assume, or stop?

**GROUP 3 — Communication**
7. How do you want to be kept updated on work in progress?
8. What's a communication pattern from AI that's wasted your time before?

**GROUP 4 — Past Mistakes**
9. What's something that went wrong in your workflow that you don't want repeated?
10. What's a rule you wish you'd had from the beginning?

**GROUP 5 — Tools & Systems**
11. What tools are you using and what are their quirks agents should know?
12. Are there any tools, files, or systems that should never be touched without your explicit approval?

---

## Template

Copy the block below — paste it into a new file called `MEMORY.md` and start adding entries.

````markdown
Copy this format for every entry. All 8 fields are required. Add new entries above the `<!-- Append above -->` marker — never edit or delete existing entries.

---

# MEMORY.md — Agent Memory Store

> Append-only trust-scored memory. Agents read this to understand preferences, past decisions, and lessons learned. Never edit existing entries — mark them `superseded` if no longer valid. New entries go above the marker at the bottom.

## Entry Format

```
## [YYYY-MM-DD] [Short descriptive title]

- **Date**: YYYY-MM-DDTHH:MM:SSZ
- **Category**: [decision | lesson | fact | preference | pattern | rule | correction]
- **Content**: [The actual thing worth remembering. Be specific.]
- **Source**: [Where this came from — user instruction, session observation, client meeting, etc.]
- **Trust Score**: [1–10]
- **Last Verified**: [YYYY-MM-DD or "unverified"]
- **Tags**: [tag1, tag2, tag3]
- **Status**: [active | archived | superseded]
```

## Trust Score Guide
| Score | Label | Agent Behavior |
|---|---|---|
| 8–10 | Critical | Use without hesitation |
| 5–7 | Important | Use, flag if high-stakes |
| 3–4 | Low priority | Verify before acting |
| 1–2 | Untrusted | Do not use without re-validation |

## Category Guide
| Category | When to use |
|---|---|
| `decision` | A choice was made — what and why |
| `lesson` | Something went wrong — what happened and the fix |
| `fact` | External information that's been verified |
| `preference` | How you want things done going forward |
| `pattern` | A recurring situation and the right response |
| `rule` | A hard rule that must always be followed |
| `correction` | An agent made a mistake — what and how to avoid it |

---

*Add new entries above this line*

<!-- Append above -->
````

---

> **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
