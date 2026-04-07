# Prompt Optimization Workflow

Use this to systematically audit and improve AI prompts that aren't performing well. The workflow identifies weak spots, tests variations, and documents what works so you can replicate the improvement across similar prompts.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in yourself

---

## LLM Instructions

Act as a prompt engineer. Interview the user about a prompt that's underperforming, diagnose the root cause, and guide them through testing and optimizing specific elements.

**SECTION 1 — Current State**

- What prompt are you trying to improve? What is it supposed to do?
- How is it currently failing? (missing information, wrong format, inaccurate, off-topic, etc.)
- How often does it fail? (always, sometimes, in certain conditions)
- What does success look like for this prompt? (specific output, format, accuracy threshold)

**SECTION 2 — Diagnosis**

- Walk me through the current prompt. Where do you think it's breaking down?
- Is the problem with clarity (the LLM misunderstands the task)?
- Is it a context problem (the LLM doesn't have enough information)?
- Is it a constraint problem (you didn't specify the output format or length)?
- Are there edge cases or variations the prompt doesn't handle?

**SECTION 3 — Optimization Targets**

- What's the one element of the prompt that, if fixed, would have the biggest impact?
- Are you providing examples? Do they clearly show the desired behavior?
- Is your output format specified? (JSON, bullet points, table, etc.)
- Are you being too vague or too verbose?

**SECTION 4 — Testing Plan**

- Can you run 3-5 test cases against the current prompt and log the results?
- For your optimization, which test cases should improve?
- What counts as a pass vs. a fail for each test case?
- How will you measure improvement? (quality score, format compliance, accuracy, etc.)

Identify the top 2-3 optimizations to test, then validate against test cases.

---

## Template

Copy the block below — paste it into a new file and fill it in.

````markdown
# Prompt Optimization: [PROMPT NAME]

**Date:** [DATE] | **Status:** [BASELINE / TESTING / OPTIMIZED]

## Current Performance
**Task:** [DESCRIPTION]
**Success metric:** [HOW YOU MEASURE SUCCESS]
**Current success rate:** [PERCENTAGE]
**Main failure mode:** [HOW IT FAILS]

## Baseline Test Results
| Test Case | Input | Expected Output | Actual Output | Pass/Fail |
|-----------|-------|-----------------|---------------|-----------|
| Case 1 | [EXAMPLE] | [EXPECTED] | [ACTUAL] | [PASS/FAIL] |
| Case 2 | [EXAMPLE] | [EXPECTED] | [ACTUAL] | [PASS/FAIL] |
| Case 3 | [EXAMPLE] | [EXPECTED] | [ACTUAL] | [PASS/FAIL] |

## Diagnosis
- **Root cause:** [CLARITY / CONTEXT / CONSTRAINTS / EDGE CASES]
- **Specific issue:** [DETAILED DESCRIPTION]

## Optimization 1: [NAME]
**Change:** [WHAT YOU'RE MODIFYING IN THE PROMPT]
**Rationale:** [WHY THIS SHOULD HELP]
**Test results:** [PASS/FAIL FOR EACH TEST CASE]

## Optimization 2: [NAME]
**Change:** [WHAT YOU'RE MODIFYING IN THE PROMPT]
**Rationale:** [WHY THIS SHOULD HELP]
**Test results:** [PASS/FAIL FOR EACH TEST CASE]

## Final Prompt
[PASTE THE OPTIMIZED PROMPT HERE]

## Improvement Summary
- Before: [OLD SUCCESS RATE / FAILURE MODE]
- After: [NEW SUCCESS RATE / FIXED BEHAVIOR]
- Replicable to: [OTHER PROMPTS WITH SIMILAR ISSUES]
````

---

> Adapted from [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) (CC0) | **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
