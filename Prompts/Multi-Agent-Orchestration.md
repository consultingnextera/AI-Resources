# Multi-Agent Orchestration

Use this to decompose a complex task across multiple AI agents, each with a specific role and expertise. The framework maps dependencies, handoffs, and verification steps to ensure the final output meets requirements.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in yourself

---

## LLM Instructions

Act as a workflow architect specializing in multi-agent systems. Interview the user about their end goal, then design an agent composition with clear roles, handoffs, and quality gates.

**SECTION 1 — End Goal & Requirements**

- What is the final deliverable you need? (report, decision, output, etc.)
- What are the key requirements for this output? (accuracy, format, timeliness, compliance)
- How will you measure whether the output is good enough?
- What happens if the agents make a mistake? Can you catch it and retry?

**SECTION 2 — Task Decomposition**

- What are the main subtasks or phases needed to reach the final output?
- Which subtasks can happen in parallel? Which must happen sequentially?
- For each subtask, what type of expertise is needed? (research, analysis, writing, validation, etc.)
- Are there any subtasks that depend on the output of previous subtasks?

**SECTION 3 — Agent Roles**

- For each subtask, what would an expert in that domain need to do?
- What context does that agent need from previous steps?
- What does that agent need to output for the next step to begin?
- Are there any handoff points where information could be lost or misunderstood?

**SECTION 4 — Quality & Verification**

- Who or what verifies each agent's output? (another agent, human review, automated check)
- What are the acceptance criteria for each stage?
- How do you handle disagreements between agents?
- Is there a final review before the output goes live?

Map out agent sequence, dependencies, handoff formats, and quality gates.

---

## Template

Copy the block below — paste it into a new file and fill it in.

````markdown
# Multi-Agent System: [PROJECT NAME]

**Date:** [DATE] | **Final Deliverable:** [DESCRIPTION]

## Agent Composition

| Agent | Role | Input | Output | Dependency | Verification |
|-------|------|-------|--------|------------|--------------|
| Agent A | [EXPERTISE] | [WHAT IT RECEIVES] | [WHAT IT PRODUCES] | [NONE / Agent X] | [WHO CHECKS] |
| Agent B | [EXPERTISE] | [WHAT IT RECEIVES] | [WHAT IT PRODUCES] | [NONE / Agent X] | [WHO CHECKS] |
| Agent C | [EXPERTISE] | [WHAT IT RECEIVES] | [WHAT IT PRODUCES] | [NONE / Agent X] | [WHO CHECKS] |

## Execution Flow
1. **Phase 1:** [AGENT A TASK] — produces [OUTPUT TYPE]
2. **Phase 2:** [AGENT B & C IN PARALLEL] — Agent B produces [OUTPUT], Agent C produces [OUTPUT]
3. **Phase 3:** [AGENT D SYNTHESIS] — integrates outputs, produces [FINAL OUTPUT]
4. **Verification:** [HUMAN REVIEW / AGENT E / AUTOMATED CHECK]

## Handoff Protocol
**Between Agent A and Agent B:**
- Format: [JSON / MARKDOWN / STRUCTURED TEXT]
- Required fields: [FIELD1, FIELD2, FIELD3]
- Quality gate: [ACCEPTANCE CRITERIA]

## Quality Checkpoints
| Checkpoint | Responsibility | Pass Criteria | Escalation |
|------------|-----------------|---------------|------------|
| [PHASE] | [AGENT / HUMAN] | [CRITERIA] | [WHO DECIDES IF IT FAILS] |

## Failure Modes & Recovery
- If [AGENT] fails: [RETRY / ESCALATE / ROUTE TO DIFFERENT AGENT]
- If [AGENT] produces low-quality output: [RERUN / HUMAN INTERVENTION]
````

---

> Adapted from [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) (CC0) | **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
