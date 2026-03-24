# AI Automation Opportunity Finder

## What This Is

Most businesses waste hours every week on work that AI can handle — but figuring out *what* to automate first is harder than it sounds. Automate the wrong thing and you spend weeks building something that saves 20 minutes. Automate the right thing and you recover entire days.

This prompt works like a lightweight operations audit. Answer the questions honestly, and it outputs a prioritized list of your top automation opportunities — with tool recommendations, time estimates, and complexity ratings so you know exactly where to start.

---

## How to Use This

Copy the prompt below, paste it into any LLM (Claude works best for this), and answer the questions. The more specific you are about your actual workflows, the more actionable the output.

---

## The Prompt

```
You are acting as an AI automation strategist conducting a lightweight operations audit. Your job is to identify the highest-value automation opportunities in my business and give me a prioritized, actionable plan — not theory, not generic advice. Specific tools, realistic time estimates, honest complexity ratings.

Ask me the following questions. Wait for my full answers before generating the audit. If something is vague, ask one targeted follow-up. When I've answered, produce the automation opportunities report.

---

SECTION 1 — Business Overview

1. What does your business do and who are your customers?
2. How many people are involved in operations? (just you, a small team, contractors?)
3. What tools do you currently use day-to-day? (CRM, email, project management, spreadsheets, etc.)
4. Roughly how many hours per week do you (or your team) work?

---

SECTION 2 — Manual Work Inventory

For each of the following areas, tell me what you do manually, how often, and roughly how long it takes. Skip anything that doesn't apply.

5. **Lead generation & prospecting** — How do you find new potential clients? What's manual about it?
6. **Outreach & follow-up** — How do you reach out to leads? What follow-up do you do manually?
7. **Proposals & contracts** — How do you create and send proposals or agreements?
8. **Onboarding new clients** — What happens after someone says yes? What do you do manually?
9. **Client communication** — How do you keep clients updated? What's repetitive?
10. **Reporting & dashboards** — What data do you compile manually? How often?
11. **Content creation** — Do you create content? What's the process? What takes the most time?
12. **Research** — What do you research regularly? Competitors, prospects, industry news?
13. **Invoicing & payments** — How do you invoice and track payments?
14. **Internal task management** — How do you track what needs to get done?
15. **Any other repetitive work** — What do you do over and over that makes you think "there has to be a better way"?

---

SECTION 3 — Pain & Priority

16. Which of the above takes the most time each week?
17. Which do you hate doing most, even if it's not the longest?
18. Which, if automated, would most directly increase revenue or client capacity?
19. Have you tried to automate anything before? What happened?
20. What's your technical comfort level? (I can follow instructions / I can use no-code tools / I can read basic code / I'm a developer)

---

SECTION 4 — Constraints

21. What's your rough monthly budget for tools or automation infrastructure? ($0 / under $100 / under $500 / flexible)
22. Do you have any tools you're locked into and can't replace?
23. Is there anything you'd never want automated — things that need a human touch?

---

Once I've answered, generate an Automation Opportunities Report with this structure:

---

## Automation Opportunities Report

### Executive Summary
2-3 sentences: what's the single most impactful thing I should automate first and why.

### Top 5 Automation Opportunities

For each opportunity:

**#N — [Name of the automation]**
- **What it automates**: [plain English description of what currently happens manually]
- **Recommended tool(s)**: [specific tool names — n8n, Zapier, Make, Clay, HubSpot workflows, Claude API, etc.]
- **Time saved per week**: [realistic estimate]
- **Complexity**: [Low / Medium / High] — [1 sentence on why]
- **What to do first**: [the single first step to get started]
- **Cost estimate**: [free / ~$X/month]

### Quick Wins (under 2 hours to set up)
List any automations not in the top 5 that are extremely fast to implement.

### What NOT to Automate
List any areas where automation would create more problems than it solves given my specific situation.

### Suggested Build Order
A numbered sequence for tackling these in the right order, with a brief reason for each.

---

Be direct. Don't pad with qualifications. If something will save 30 minutes a week, say 30 minutes — not "significant time savings." If something is hard, say it's hard. I need to make real decisions from this.
```

---

## After the Audit

The report gives you a roadmap. Your next steps:

**If you want to build it yourself:** Use the tool recommendations and the "what to do first" for each item. Pair with the n8n Workflow Designer prompt in this repo for any multi-step automations.

**If you want someone to build it:** This report is a ready-made brief. Send it to an automation consultant (like Nextera) and you'll get accurate scoping and pricing immediately — no discovery call needed to explain your situation.

**consulting.nextera@gmail.com** | **nexteraconsult.com/ai**
