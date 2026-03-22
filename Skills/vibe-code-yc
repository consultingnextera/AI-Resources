---
name: vibe-code
description: Guide any AI-assisted coding session using the YC vibe coding methodology. Use this skill whenever the user is starting a new build, setting up an AI coding environment, stuck mid-build, debugging, or asking how to structure a coding project. Covers planning, version control, testing, bug fixing, tool optimization, tech stack decisions, and continuous improvement. Trigger for any request involving Cursor, Windsurf, Claude Code, or any AI-assisted development workflow.
---

# Vibe Code Skill

Structure and guide AI-assisted coding sessions using the YC vibe coding methodology. Use this skill at the start of a build, when stuck, or when the user wants to level up how they work with AI coding tools.

Identify where the user is in their build and jump to the relevant section. Don't recite the whole skill — use the relevant parts for the situation.

---

## Section 1 — Planning

Start here before writing a single line of code.

- **Create a comprehensive plan first**: Work with the AI to write a detailed implementation plan in a markdown file before touching the codebase
- **Review and refine**: Delete unnecessary items, mark features as "won't do" if too complex
- **Maintain scope control**: Keep a separate section in the plan for ideas-for-later — don't let them creep into the current build
- **Implement incrementally**: Work section by section rather than attempting to build everything at once
- **Track progress**: Have the AI mark sections as complete after successful implementation
- **Commit regularly**: Ensure each working section is committed to Git before moving to the next

---

## Section 2 — Version Control

- **Use Git religiously**: Don't rely on AI tools' revert functionality — it's not reliable enough
- **Start clean**: Begin each new feature with a clean Git slate
- **Reset when stuck**: Use `git reset --hard HEAD` when the AI goes on a vision quest and breaks things
- **Avoid cumulative problems**: Multiple failed fix attempts create layers and layers of bad code — stop and reset
- **Clean implementation**: When you finally find the right solution, reset and implement it cleanly — don't patch it onto broken code

---

## Section 3 — Testing

- **Prioritize high-level tests**: Focus on end-to-end integration tests over unit tests
- **Simulate user behavior**: Test features by simulating someone actually clicking through the site or app
- **Catch regressions**: LLMs often make unnecessary changes to unrelated logic — tests catch this
- **Test before proceeding**: Ensure tests pass before moving to the next feature
- **Use tests as guardrails**: Start with test cases before building — they provide clear boundaries for the AI to work within

---

## Section 4 — Bug Fixing

- **Leverage error messages**: Copy-pasting the full error message directly is often enough — let the AI work from it
- **Analyze before coding**: Ask the AI to consider multiple possible causes before jumping to a fix
- **Reset after failures**: After each unsuccessful fix attempt, start with a clean slate — don't layer attempts
- **Implement logging**: Add strategic logging to understand what's actually happening at runtime
- **Switch models**: When one model gets stuck in a loop or keeps suggesting the same broken approach, switch to a different one
- **Clean implementation**: Once the fix is identified, reset and implement it cleanly on a fresh codebase state

---

## Section 5 — AI Tool Optimization

- **Write instruction files**: Create detailed instructions for your AI tools in the appropriate files — `cursor.rules`, `windsurf.rules`, `claude.md` — the more context, the better the output
- **Download API docs locally**: Put API documentation in your project folder so the AI works from accurate, current references
- **Use multiple tools**: Some founders run Cursor and Windsurf simultaneously on the same project — different tools, different strengths
- **Tool specialization**: Cursor is faster for frontend work; Windsurf thinks longer and is better for complex backend logic
- **Compare outputs**: Generate multiple solutions from the same prompt and pick the best one — don't just take the first answer

---

## Section 6 — Complex Feature Development

- **Build standalone prototypes first**: Build complex features in a clean, separate codebase before integrating — easier to debug and iterate
- **Use reference implementations**: Point the AI to working examples to follow — don't ask it to invent from scratch when a pattern exists
- **Clear boundaries**: Maintain consistent external APIs while allowing internal changes — this prevents breaking downstream dependencies
- **Modular architecture**: Service-based architectures with clear boundaries work better than monorepos for AI-assisted development — easier to reason about, easier for the AI to work within

---

## Section 7 — Tech Stack

- **Established frameworks excel**: Frameworks like Ruby on Rails have 20 years of consistent conventions in the AI's training data — less ambiguity, better output
- **Training data matters**: Newer languages like Rust or Elixir may have less AI training data — factor this in when choosing a stack for an AI-heavy build
- **Modularity is key**: Small, modular files are easier for both humans and AIs to work with — avoid large files at all costs
- **Avoid large files**: Files that are thousands of lines long are harder to reason about, harder to debug, and harder for AI to navigate accurately

---

## Section 8 — Beyond Coding

AI tools can do more than write code in your sessions:

- **DevOps automation**: Use AI for configuring servers, DNS, and hosting — not just application code
- **Design assistance**: Generate favicons, icons, and UI elements directly in the session
- **Content creation**: Draft documentation and marketing materials while the context is fresh
- **Educational tool**: Ask the AI to explain its implementations line by line — best way to learn what was built
- **Use screenshots**: Share UI bugs or design inspiration visually — faster than describing in text
- **Voice input**: Tools like Aqua enable ~140 words per minute input — significantly faster than typing for longer prompts

---

## Section 9 — Continuous Improvement

- **Refactor regularly**: Once tests are in place, refactor frequently — clean code is easier for AI to extend
- **Identify opportunities**: Ask the AI to scan the codebase and find refactoring candidates
- **Stay current**: Try every new model release — capabilities change quickly and a new model may handle your stack better
- **Recognize strengths**: Different models excel at different tasks — learn which ones are best for your specific use cases and route accordingly
