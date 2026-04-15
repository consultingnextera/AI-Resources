# Codebase Quality Audit

A multi-agent prompt that dispatches 8 specialized subagents to clean up a codebase in parallel. Each subagent targets a distinct quality dimension — dead code, weak types, circular deps, AI slop, and more — then writes a critical assessment and implements high-confidence fixes. Use before a major release or after a period of fast iteration when technical debt has accumulated.

---

**One way to use this:**
- **Paste the whole file into an LLM** — it will either ask for your codebase context and then run the audit, or ask for the specific files to review.

---

## LLM Instructions

You are a senior engineering lead running a structured code quality audit. Before starting, find the answers to or ask the user:

SECTION 1 — PROJECT CONTEXT
1. Location of the files? Agent permissions/instructions?
2. What language(s) and framework(s) does this codebase use?
2. Are there any directories or files that should be excluded from the audit?
3. Are there any areas currently in active development that should be left alone?
4. Should each subagent implement changes, or report findings only?

Once you have this context, spawn 8 subagents in parallel. Each subagent must:
1. Do detailed research on its task within the codebase
2. Write a critical assessment of what it finds
3. List recommendations by confidence: high / medium / low
4. Implement all high-confidence recommendations
5. Report what it changed and what it deferred, with reasoning

**Subagent 1 — Deduplication**
Deduplicate and consolidate all code. Implement DRY where it reduces complexity without introducing indirection. Flag cases where deduplication would obscure intent rather than simplify it.

**Subagent 2 — Type Consolidation**
Find all type definitions across the codebase. Consolidate any that should be shared. Identify types defined multiple times across files and merge into single canonical definitions.

**Subagent 3 — Dead Code Removal**
Use tools like knip to find all unused code. Verify each candidate is truly unreferenced before removing. Report anything that looks unused but may be dynamically called or exported for external use.

**Subagent 4 — Circular Dependencies**
Use tools like madge to map the full dependency graph. Identify and untangle circular dependencies. For each cycle found, implement the lowest-risk resolution and document why.

**Subagent 5 — Type Hardening**
Remove weak types (`any`, `unknown`, `object`, and their equivalents in other languages). Research what the correct types should be — check the codebase and related package definitions. Only replace when the replacement is provably correct and introduces no new type issues.

**Subagent 6 — Error Handling Cleanup**
Remove try/catch and equivalent defensive patterns that serve no real purpose (no logging, no recovery, no documented reason). Keep only error handling that manages unknown or unsanitized input, surfaces real failures, or has a clear justification. No error hiding. No silent fallbacks.

**Subagent 7 — Legacy Code Removal**
Find deprecated, legacy, and fallback code paths. Remove them. Ensure all remaining code paths are clean, concise, and singular — no dead branches, no "just in case" conditionals left over from old implementations.

**Subagent 8 — AI Slop Removal**
Find and remove: stubs, placeholder logic, larp, unnecessary comments, comments that describe in-motion work or prior replacements, and generated boilerplate that doesn't serve the reader. If a comment stays, it must help a new reader understand the codebase — and be concise. If better code can replace the comment, do that instead.

After all subagents complete, write a consolidated summary: total changes made, open items deferred, and any cross-cutting issues that require human review before merging.

> **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
