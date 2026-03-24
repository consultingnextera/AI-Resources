# OpenClaw Skill Conversion Prompt

## Context

I am uploading 5 skill files that were originally built for Claude.ai's skill system. I need you to convert them into native OpenClaw vault files that match the conventions of my existing PersonalOS vault. Below is everything you need to know to do this correctly.

---

## The 5 Skills Being Converted

1. `vibe-code` — YC vibe coding methodology for AI-assisted coding sessions
2. `frontend-design` — Frontend design and build guidance
3. `workflow-creator` — Full automation workflow lifecycle (design → build → document)
4. `linkedin-content` — LinkedIn content creation in your founder voice
5. `client-deliverable` — Client-facing documents (proposals, SOWs, project updates, etc.)

---

## My Vault Conventions — Match These Exactly

### YAML Frontmatter
Every file in my vault uses this schema. Reformat every skill to match:

```yaml
---
title: "SKILL_NAME"
status: active
domain: [system | content | code | business]
updated: [today's date in YYYY-MM-DD]
tags: [skill, relevant-tags]
read_when:
  - [specific condition that should trigger an agent to load this file]
  - [another condition if applicable]
---
```

The `read_when` field is critical — it tells agents when to load this file without Zeus having to hardcode it. Be specific. Example: `"When Daedalus receives any frontend build or UI task"` not just `"frontend tasks"`.

### Internal File References
Use wiki-style links for all internal vault references:
- `[[NEXTERA.md]]` not "see NEXTERA.md"
- `[[memory/VOICE_PROFILE.md]]` not "load voice profile"
- `[[agents/REGISTRY.md]]` etc.

### File Location
All 5 skills go into: `~/PersonalOS/skills/`
Filename format: `SKILL_NAME.md` (all caps, matching vault convention)

---

## Agent Routing — Wire Each Skill to the Right Agent

After converting the files, update `agents/REGISTRY.md` to add a `read_when` or boot sequence entry for each skill under the relevant agent. The routing is:

| Skill | Primary Agent | When to Load |
|---|---|---|
| `vibe-code` | Daedalus | Any coding, debugging, or build task |
| `frontend-design` | Daedalus | Any frontend, UI, landing page, or web build task |
| `workflow-creator` | Daedalus + Athena | Any automation build, n8n workflow, or AI pipeline task |
| `linkedin-content` | Calliope | Any LinkedIn post, content creation, or social media task |
| `client-deliverable` | Athena | Any proposal, SOW, discovery recap, project update, or client doc task |

Add these to the **Boot Sequence** or **Context Files** section of each agent's definition in `REGISTRY.md`. Do not add new agents — wire into existing ones only.

---

## NEXTERA.md Handling — Remove Bundled Copies

`linkedin-content` and `client-deliverable` currently include their own bundled copy of `NEXTERA.md`. Remove those embedded copies. Replace all references with `[[NEXTERA.md]]` pointing to the real file that already exists in the vault root.

---

## Voice Profile — Calliope Specific

`linkedin-content` currently references `NEXTERA.md` for voice guidance. Inside OpenClaw, Calliope uses `memory/VOICE_PROFILE.md` as the authoritative voice source. In the converted `linkedin-content` skill:

- Replace any "load NEXTERA.md for brand voice" instructions with `[[memory/VOICE_PROFILE.md]]`
- Keep `[[NEXTERA.md]]` references only for business facts (proof points, pricing, client names)
- The skill should function as a **format and hook reference** that Calliope reads during her Step 4 (generate full package) — it should complement her existing workflow, not replace it
- Do not duplicate Calliope's existing brief → duplicate check → generate → revision loop. The skill provides the LinkedIn-specific format rules and voice calibration only.

---

## SKILLS_INDEX.md

Check whether `skills/SKILLS_INDEX.md` exists in the vault.

**If it exists:** Append all 5 new skills to it with this format:
```markdown
| [[SKILL_NAME.md]] | [one sentence description] | [primary agent] | [date added] |
```

**If it does not exist:** Create `skills/SKILLS_INDEX.md` with this structure:
```markdown
---
title: "SKILLS INDEX"
status: active
domain: system
updated: [today's date]
tags: [skills, index, reference]
---

# Skills Index

Reference list of all skills available to agents in this vault.

| Skill | Purpose | Primary Agent | Added |
|---|---|---|---|
| [[VIBE-CODE.md]] | YC vibe coding methodology for AI-assisted sessions | Daedalus | [date] |
| [[FRONTEND-DESIGN.md]] | Frontend design and build standards | Daedalus | [date] |
| [[WORKFLOW-CREATOR.md]] | Automation workflow lifecycle — design to documentation | Daedalus, Athena | [date] |
| [[LINKEDIN-CONTENT.md]] | LinkedIn content format and voice calibration | Calliope | [date] |
| [[CLIENT-DELIVERABLE.md]] | Client-facing documents — proposals, SOWs, updates | Athena | [date] |
```

---

## REFERENCE.md Update

Add all 5 skills to the `REFERENCE.md` skills section under the vault consistency rules. Match the existing table format used in that file.

---

## Structural Changes Per Skill

### vibe-code + frontend-design
- Minimal changes: reformat frontmatter, add `read_when`, add vault links where relevant
- No NEXTERA or voice references to update
- Add to Daedalus boot sequence in REGISTRY.md

### workflow-creator
- Reformat frontmatter, add `read_when`
- In Phase 4 (client documentation), add reference to `[[CLIENT-DELIVERABLE.md]]` as the formatting standard for the output doc
- Wire to both Daedalus (build phase) and Athena (planning phase) in REGISTRY.md

### linkedin-content
- Reformat frontmatter, add `read_when`
- Remove bundled NEXTERA.md copy
- Replace voice references with `[[memory/VOICE_PROFILE.md]]`
- Keep business fact references pointing to `[[NEXTERA.md]]`
- Restructure as a Calliope reference file, not a standalone workflow
- Wire into Calliope's Context Files in REGISTRY.md

### client-deliverable
- Reformat frontmatter, add `read_when`
- Remove bundled NEXTERA.md copy
- Replace with `[[NEXTERA.md]]` links to specific sections (Section 3 for proof points, Section 5 for pricing, Section 8 for voice)
- Wire into Athena's Context Files in REGISTRY.md

---

## Git Commit

After all changes are complete, commit with:
```
[skills] add 5 converted skills from Claude skill system to vault
```

Vault-only changes — commit directly to main per `loops/SAFETY_RULES.md`.

---

## Definition of Done

- [ ] All 5 skill files are in `~/PersonalOS/skills/` with correct vault frontmatter
- [ ] All internal references use `[[wiki-link]]` format
- [ ] No bundled NEXTERA.md copies remain in any skill file
- [ ] `agents/REGISTRY.md` updated with boot/context entries for all 5 skills
- [ ] `skills/SKILLS_INDEX.md` exists and lists all 5 skills
- [ ] `REFERENCE.md` updated to include skills section
- [ ] Changes committed to main with correct commit message
-e 
---

> **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
