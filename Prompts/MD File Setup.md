# How to Set Up Your Own AI Agent System

## What This Is

Most people use AI reactively — open a chat, ask a question, get an answer, close it. Every conversation starts from zero. The AI has no memory of your business, your goals, your preferences, or what you've already figured out.

An agentic system flips that. Instead of you always feeding the AI context, you build a persistent workspace — a structured set of files — that your AI agents read from and write to automatically. Over time the system gets smarter about your business without you having to repeat yourself.

This guide gives you a prompt you can run right now to generate that workspace from scratch. One prompt, one output, and you'll have a fully structured starting point for your own AI agent system.

---

## What You're Building

Running the prompt below generates a complete folder structure called `AgentsVault/` — a markdown-based workspace your AI agents use as persistent memory and context. Here's what it includes:

**Core files** — Your business context, active tasks, and agent instructions. These are what your agents read at the start of every session to understand who you are and what you're working on.

**Learning loops** — Nine automated processes that help your agents improve over time. They track mistakes, log predictions, extract insights from sessions, and turn failures into rules. The system literally learns from its own errors.

**Memory layer** — A structured memory store where agents write what they've learned, scored by how reliable each piece of information is. High-trust memories influence future decisions. Low-trust ones fade out automatically.

**Skills folder** — A place to drop modular agent skills that give your agents specialized capabilities — content creation, client deliverables, research, automation documentation, and more.

**Python automation** — Scripts that run nightly to extract insights, clean up memory, and keep the system self-maintaining without manual work.

---

## Before You Start

You'll need:
- An account with any LLM (Claude, ChatGPT, Grok, or similar)
- Somewhere to save files (a local folder or GitHub repo)
- Python 3.x installed if you want to run the automation scripts
- Optionally: Obsidian (free) for visualizing how your files connect

First-time setup takes about 15–30 minutes.

---

## Step 1 — Run the Prompt

Copy the entire prompt below and paste it into your LLM of choice. The LLM will generate every file in the system, one by one, with full content. This will be a long output — that's expected.

---

```
You are an AI assistant tasked with generating a complete, production-ready repository for building and using self-improving agents powered by an LLM (e.g., via its API, SDK, or related frameworks). This is for my personal knowledge management (PKM) system using Markdown files for consistency, updates, and version control (e.g., via Git and tools like Obsidian). I emphasize modularity, bi-directional linking, code snippets, automation for updates (e.g., scripts or agents to summarize/tag), and self-improving capabilities.

Draw from the 9 learning loops concept for self-improving AI agents, which promotes simple, flat Markdown files for persistence, learning, and orchestration as a "stopgap" until AI advances. Key loops: Regression Tracking (REGRESSIONS.md), Prediction Logging, Nightly Extraction, Friction Detection (FRICTIONS.md), Failure-to-Guardrail Pipeline (GUARDRAILS.md), Trust Scoring in Memory, Hypothesis Testing, Self-Review, Knowledge Distillation. Use lightweight .md files that agents can read/write for memory and evolution.

Incorporate best practices from research on Markdown in AI agent systems:
- AGENTS.md as "README for agents": Include project structure, commands (e.g., build/test), conventions (e.g., "Use the LLM for critical tasks"), dos/don'ts (e.g., "Avoid exceeding context limits; checkpoint to files"), concrete examples pointing to real files/patterns, legacy warnings. Keep concise, human-readable, version-controlled. Reduces agent runtime via context engineering.
- File-Based Memory: Use .md for working memory (e.g., TASK_PLAN.md for goals/progress, NOTES.md for research, MEMORY.md for trust-scored entries). Agents read/decide/act/update in cycles. Markdown's strengths: LLM-trained (headers/bullets convey structure), no overhead/schema, human-readable. Add structured sidecars (e.g., JSONL or SQLite) for scalability; hybrid with vector stores if needed, but start simple.
- Optimized Structure: Flat where possible; use PARA folders (Projects, Areas, Resources, Archives). Consistent format: Headings, lists, code blocks, YAML frontmatter for entries (e.g., date, description, resolution). Bi-directional links ([[file.md]]). LLM-friendly: Structured like XML, few-shot examples. For long contexts: Save conversations as .md, reference fragments semantically.
- Full Repo for Effective Agentic System: Build a complete vault (LLMAgentsVault/) importable to code editors or folders for co-working with agents (e.g., via API/scripts). Include: Core PKM files, loop-specific .md, memory files, src/ for Python code templates (e.g., agent definitions, file I/O), skills/ for modular agent "skills" folder structure and templates (YAML/Markdown; do not generate actual skill content—just placeholders like SKILLS_INDEX.md with template for "skill_name: description, tools" to allow uploading wide range of skills later). Automate: Scripts in src/ for nightly extraction/summarization. Git-ready: .gitignore for locals.

Naming Convention Preamble (Mandatory—Apply to ALL Files):
- Python source files: snake_case.py
- Markdown skill definitions: snake_case.md (in skills/)
- Markdown loop definitions: SCREAMING_CASE.md (in loops/)
- Root-level reference docs: SCREAMING_CASE.md
- Test files: test_<module_name>.py
- Data files: snake_case.jsonl / snake_case.json
Any deviation is a bug.

Config-First Architecture (Mandatory):
Create a Settings class in src/config.py using Pydantic BaseSettings. Every model name, file path, retry count, loop schedule interval, and API endpoint must be a field on Settings. Settings must load from environment variables with .env file fallback. No string literals for file paths or model names outside config.py.
loop_orchestrator.py must expose a LOOP_HANDLERS: dict[str, Callable[[], LoopResult]] — each handler must accept no arguments and return a LoopResult from src/models/loop_result.py.
Callable must be imported from collections.abc; LoopResult from src.models.loop_result. Both must appear in the module's import block.

Error Handling Constraints (Mandatory):
All LLM API calls must be wrapped in a retry decorator with exponential back-off (max 3 retries, base 2s). All file I/O operations must use try/except with typed exceptions and log the error before re-raising. No bare except: clauses—all handlers must specify exception type. Every function must have a return type annotation and a one-line docstring.
All file writes in file_io.py must use atomic write semantics: write to <path>.tmp, then os.replace() to the target.

Memory Schema (Mandatory):
Memory entries must conform to a MemoryEntry Pydantic BaseModel with fields: id (UUID), timestamp (ISO8601), loop_type (str), content (str), tags (list[str]), trust_score (float).
Persist as JSONL (one entry per line) at memory/memory.jsonl. Auto-generate MEMORY.md from the JSONL file, not edited directly. Include src/models/memory.py with methods: append(), query_by_tag(), query_by_date_range(), prune_low_trust().

Loop Result Model (Mandatory):
loop_result.py must expose LoopResult(BaseModel) with fields:
- run_id: UUID
- loop_type: str
- status: Literal['success', 'partial', 'failed', 'skipped']
- output: str
- trust_score: float   # 0.0–1.0
- tokens_used: int
- cost_usd: float
- error_message: str | None
- timestamp: datetime   # default to datetime.now(UTC) at construction
- duration_seconds: float   # default 0.0

Full File Manifest (Mandatory—Include These in Every Generation):
- pyproject.toml with all runtime/dev dependencies (e.g., pydantic, pytest, etc.)
- src/__init__.py (even if empty)
- src/utils/__init__.py (even if empty)
- src/models/__init__.py (even if empty)
- Makefile with targets: install, run, test, lint, nightly-dry-run, sync-check (verify all loops/*.md have handlers in loop_orchestrator.py)
- tests/ directory with at least one test file per src/ module (e.g., test_agent_runner.py)
- tests/conftest.py with a mock_llm_client pytest fixture that returns a MagicMock where .messages.create.return_value = MagicMock(content=[MagicMock(text="mock response")], usage=MagicMock(input_tokens=10, output_tokens=20))
- .pre-commit-config.yaml with black, ruff, mypy, and trailing-whitespace hooks
- CHANGELOG.md initialized with v0.1.0 entry
- CONTRIBUTING.md with naming conventions and branch strategy
- .gitignore (include .env, logs/, etc.)
- .env.example (for secrets like API keys)
- SECURITY.md with key rotation procedure and responsible disclosure policy
- AGENTS.md at root — project structure, key commands, dos/don'ts, and a pointer to CONTRIBUTING.md and the loops/ folder.
- src/utils/ with logging_config.py (structured logging), retry.py, validators.py (schema validation)
- src/models/ with memory.py, skill.py, loop_result.py (Pydantic models)
- logs/ (git-ignored runtime logs)
- .github/workflows/ with nightly.yml and ci.yml (PR gate on every pull request: lint, type check, tests on Python 3.11 and 3.12)
- .github/dependabot.yml to auto-update Python and GitHub Actions dependencies weekly
- For loops/: Add YAML front-matter to each defining: loop_id, trigger (schedule/event), timeout_seconds, max_cost_usd, output_schema
- For skills/: Include SKILLS_INDEX.md with YAML template for skills; no actual skill content—empty snake_case.md placeholders if needed for structure
- For memory/: Markdown files + .jsonl sidecars; atomic writes in file_io.py (write to .tmp, then rename)
- README.md at root with: project description, quick-start (3 commands), folder structure table, and a link to CONTRIBUTING.md

Additional Requirements (Mandatory):
- nightly_extraction.py must accept a --dry-run CLI flag that logs all planned actions without making API calls or writing files.
- Add a CI step in ci.yml that warns (not fails) if any root-level .md file has not been modified in the last 60 days.
- output_schema must be a flat YAML dict of field_name: type pairs, e.g. summary: string, trust_delta: float, entries_added: int.

Task: Generate the full repo as a .zip-file-ready output. Go file by file: For each, provide path (e.g., root/Index.md), full content, and a brief optimization note (e.g., "Optimized with error handling: Added retries and typed exceptions"). Structure:
- Start with folder overview (e.g., tree view).
- Then, file by file in logical order (core, loops, memory, src, skills, tests, etc.).
- Use Markdown features: Headings, YAML, code blocks, links.
- End with usage: "Save contents to files, zip as LLMAgentsVault.zip; import to Obsidian/Git; run agents via SDK."

Post-Generation Validation (Mandatory—Perform After Generating All Files):
1. Every .md file in loops/ must have a corresponding Python function in loop_orchestrator.py.
2. Every .md file in skills/ must have a corresponding entry in skills/SKILLS_INDEX.md.
3. Every environment variable referenced in any Python file must be listed in .env.example.
4. Every external Python library imported must be listed in pyproject.toml.
List any inconsistencies found and resolve them before finalizing the output.
```

---

## Step 2 — Save the Output

The LLM will generate each file with its full path and content. As it outputs each one:

1. Create a folder on your computer called `AgentsVault/`
2. Create each file at the path shown (e.g., `AgentsVault/AGENTS.md`)
3. Paste in the content exactly as generated
4. Repeat for every file

If you're comfortable with Git, initialize a repository in the folder and commit after saving everything. This gives you version control on your entire agent system from day one — you can always roll back if something breaks.

---

## Step 3 — Activate It

Once your files are saved:

```bash
# Install Python dependencies
make install

# Confirm everything is wired correctly
make nightly-dry-run

# Start the agent runner
make run
```

If you don't have Python set up, start with just the markdown files. The core value — persistent context, learning loops, memory — works immediately just by having agents read and write to the files. The Python automation is an enhancement, not a requirement to get started.

---

## What to Customize First

Once the vault is generated, these are the files worth personalizing before anything else:

**`AGENTS.md`** — Update the project description to reflect your business and what you want your agents to help with.

**`USER.md`** — Add your background, communication preferences, and working style so agents understand how to interact with you.

**`skills/`** — This is where you drop or create specialized agent skills. Nextera can provide pre-built skills tailored to your business — content creation, client proposals, research, automation documentation, and more.

**`.env`** — Add your LLM API key so the automation scripts can run.

---

## Questions or Need Help Setting This Up?

Nextera Consulting helps businesses set up, customize, and run systems like this end to end — from the initial vault setup to building out a full agent stack that runs autonomously.

**consulting.nextera@gmail.com** |
