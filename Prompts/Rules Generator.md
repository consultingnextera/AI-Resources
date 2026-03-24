# Cursor Rules Generator

## What This Is

AI coding tools like Cursor, Windsurf, and Claude Code are dramatically better when they understand your project — your stack, your conventions, what you've already tried, and what you never want them to do.

Without a rules file, every session starts cold. The AI makes generic decisions, picks the wrong patterns, and repeats mistakes you've already corrected.

This prompt generates a `cursor.rules` (or `claude.md` / `windsurf.rules`) file tailored to your specific project. Paste it in once. Your AI coding sessions get measurably better immediately.

---

## Which File to Create

| Tool | File Name | Location |
|---|---|---|
| Cursor | `cursor.rules` | Project root |
| Windsurf | `windsurf.rules` | Project root |
| Claude Code | `CLAUDE.md` | Project root |
| Any tool | `AI_CONTEXT.md` | Project root |

The content is the same — just rename based on your tool.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in directly

---

## LLM Instructions

Read this file, then conduct the following interview with me. Ask one section at a time and wait for my answers. When I've answered everything, fill out the template at the bottom of this file.

---

You are helping me generate an AI coding rules file for my project. This file will be loaded by my AI coding assistant (Cursor, Windsurf, Claude Code, or similar) at the start of every session so it understands my project without me having to re-explain anything.

Ask me the following questions. Wait for my answers before generating anything. If my answers are incomplete, ask one targeted follow-up. When I've answered everything, generate the complete rules file.

---

SECTION 1 — Project Overview

1. What does this project do? Give me the one-paragraph description.
2. What's the current state? (brand new, early prototype, live in production, being refactored)
3. Who uses it? (just me, a team, external users, clients)

---

SECTION 2 — Tech Stack

4. What's the primary programming language?
5. What framework(s) are you using? (React, Next.js, Express, Rails, FastAPI, etc.)
6. What database(s)? (Postgres, SQLite, Supabase, MongoDB, etc.)
7. How is it deployed or hosted? (Vercel, Railway, VPS, local only, etc.)
8. Any other key dependencies or services? (auth system, payment processor, third-party APIs, etc.)

---

SECTION 3 — File & Folder Structure

9. Describe the top-level folder structure. What's in each main folder?
10. Where does the main application logic live?
11. Are there any folders the AI should never touch or should treat as read-only?
12. Is there a naming convention for files? (kebab-case, camelCase, feature-based, etc.)

---

SECTION 4 — Coding Conventions

13. Do you prefer functional or class-based components/patterns?
14. How do you handle state? (local state, global store, server state, etc.)
15. Do you use TypeScript? If so, how strictly typed?
16. What's your approach to error handling?
17. Do you write tests? If so, what kind and with what framework?
18. Any linting or formatting tools? (ESLint, Prettier, Black, etc.)

---

SECTION 5 — What the AI Gets Wrong

19. What's the most common mistake your AI coding tool makes on this project?
20. What patterns does it suggest that you always reject?
21. Has it ever broken something specific that you had to fix? What was it?
22. What does it tend to over-engineer that should be simple?

---

SECTION 6 — What the AI Should Always Do

23. What conventions should it always follow? (e.g., always use async/await, always add error handling, always write comments for non-obvious logic)
24. Should it always ask before touching certain files or systems?
25. How should it handle database changes? (always create migrations, never modify schema directly, etc.)
26. What's your git workflow? (feature branches, commit directly to main, PR required, etc.)

---

SECTION 7 — Current Focus

27. What are you actively building or fixing right now?
28. What's the next feature or fix after that?
29. Are there any known bugs or issues the AI should be aware of?
30. Anything that's intentionally left unfinished or marked as TODO that it should not touch?

---

Once I've answered, generate a complete rules file with these sections:

# Project Overview
# Tech Stack
# Folder Structure & File Naming
# Coding Conventions
# What To Always Do
# What To Never Do
# Current Focus
# Known Issues & Workarounds
# Git & Deployment Rules

Write it in plain, direct language — instructions not descriptions. Use bullet points and short sentences. The AI reading this file needs to apply these rules, not understand the philosophy behind them.

Flag any gaps where more detail from me would make the rules more effective.

---

## Tips for Better Rules

**Be specific about mistakes.** "Don't add unnecessary abstractions" is vague. "Don't create a separate utility file for a function that's only used once" is actionable.

**Update it as the project evolves.** Add a new rule every time you correct the same mistake twice. If you're fixing the same thing repeatedly, it belongs in the file.

**Add a "Current Focus" section every session.** Even if the main file is static, add a few lines at the top of each session describing what you're working on today. This dramatically improves relevance.

**Different tools, same file.** You can maintain one file and symlink or copy it to whatever filename your tool needs.

---

## After You Have the File

**Drop it in your project root.** Cursor, Windsurf, and Claude Code all pick up their respective rules files automatically when they exist in the root directory — no configuration needed.

**Test it immediately.** Ask your AI tool to do something it previously got wrong. If the rule is in the file and it still makes the same mistake, the instruction was too vague — tighten it.

**Start a session by referencing it.** Some tools load it automatically; others need a nudge. Starting with "read the rules file before we begin" takes two seconds and ensures the context is loaded.

**Commit it to git.** This file is part of your project. It should live in version control so it stays in sync as the project evolves and so collaborators benefit from it too.

**Treat it as a living document.** The first version won't be perfect. Every time you correct your AI coding tool, ask yourself: "should this be in the rules file?" If you've corrected the same thing more than once — yes.


---

## Template

If you'd rather fill this in yourself, copy and paste this into your project root as `cursor.rules`, `windsurf.rules`, or `CLAUDE.md`:

```markdown
# Project Overview
[One paragraph: what this project does, who uses it, current state]

# Tech Stack
- Language: 
- Framework: 
- Database: 
- Hosting: 
- Key dependencies: 

# Folder Structure
[Describe your top-level folders and what lives in each]

# Coding Conventions
- Components: [functional / class-based]
- State management: 
- TypeScript: [yes/no, strict/loose]
- Error handling: 
- Tests: [yes/no, framework]

# What To Always Do
- 
- 
- 

# What To Never Do
- 
- 
- 

# Current Focus
[What you're actively building or fixing right now]

# Known Issues & Workarounds
[Any bugs, edge cases, or intentional TODOs the AI should know about]

# Git & Deployment
- Branch strategy: 
- Commit format: 
- Deploy process: 
```

---

> **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
