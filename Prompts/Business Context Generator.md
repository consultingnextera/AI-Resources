# Business Context Generator

## What This Is

Most AI tools give generic output because they don't know anything about your business. This prompt fixes that. Run it once, save the output as `business.md`, and load it into any AI tool — Claude, ChatGPT, Cursor, your agent system — so every interaction starts with full context instead of from zero.

The output file becomes your business's persistent AI memory.

---

## How to Use This

Copy the prompt below and paste it into any LLM. Answer each question as honestly and specifically as you can — the more detail you give, the more useful the output. You can answer in bullet points, stream of consciousness, or full sentences. The AI will structure it.

When you're done, save the output as `business.md` and keep it somewhere easy to access.

---

## The Prompt

```
You are helping me create a persistent business context file — a markdown document I'll load into AI tools so they always understand my business without me having to re-explain it every session.

Interview me by asking the following questions one group at a time. Wait for my answers before moving to the next group. Ask follow-up questions if my answers are vague or missing key details. When I've answered everything, generate the complete business.md file.

---

GROUP 1 — The Business

1. What's your business name and one-line description of what you do?
2. What legal structure is it? (LLC, sole prop, S-corp, etc.)
3. Where are you based?
4. How long have you been operating?
5. Is this your only business, or do you run multiple?

---

GROUP 2 — What You Do

6. What are your core services or products? List them all.
7. What does a typical engagement look like from start to finish?
8. What do you NOT do — what's explicitly out of scope?
9. What tools or tech do you use to deliver your work?

---

GROUP 3 — Who You Serve

10. Describe your ideal client in detail. Industry, size, role of the decision-maker.
11. What problem are they experiencing when they find you?
12. What does success look like for them after working with you?
13. Who is NOT a good fit? What signals tell you to walk away?
14. Name 2-3 current or past clients if comfortable. What did you do for them?

---

GROUP 4 — Pricing & Business Model

15. How do you charge? (hourly, project, retainer, productized, etc.)
16. What's your typical project range or starting price?
17. What's your minimum engagement?
18. How do clients usually find you? (referrals, content, outbound, etc.)

---

GROUP 5 — Proof & Positioning

19. What results have you delivered for clients? Be specific — numbers, outcomes, before/after.
20. What makes you different from alternatives? (other consultants, agencies, DIY)
21. What do clients say about working with you?

---

GROUP 6 — Voice & Communication

22. How would you describe your communication style? (direct, warm, technical, casual, etc.)
23. What words or phrases do you overuse that you'd like to avoid?
24. What tone do you want to strike in written communication? Give an example if you have one.
25. What does "bad" writing from your business look like? What should it never sound like?

---

GROUP 7 — Goals & Strategy

26. What are your top 3 business priorities right now?
27. What does success look like in 12 months?
28. What's your biggest constraint? (time, money, leads, team, etc.)
29. What would you build or do if you had 10x the resources?

---

GROUP 8 — You (The Founder)

30. What's your background? How did you get here?
31. What do you spend most of your time on day-to-day?
32. What do you want to spend less time on?
33. What's your role in the business long-term — operator, visionary, both?

---

Once I've answered all groups, generate a complete business.md file with these sections:

## Company Overview
## Services
## Ideal Client Profile (ICP)
## Pricing & Business Model
## Proof Points & Results
## Competitive Positioning
## Brand Voice & Tone
## Strategic Priorities
## Founder Background
## How to Use This File (instructions for AI tools loading this context)

Format it cleanly in markdown. Use specific language from my answers — not generic business-speak. Every section should feel like it was written by someone who actually knows this business.

At the end, flag any sections where my answers were thin and suggest what additional detail would make the file more useful.
```

---

## What to Do With the Output

1. Save it as `business.md` in a place you can find it
2. Upload it to any AI tool at the start of a session — Claude, ChatGPT, Cursor, etc.
3. For persistent use: add it to your agent vault as a core context file
4. Update it quarterly or whenever your services, pricing, or positioning changes

The more specific your answers during the interview, the more useful the output. Don't rush it — a good `business.md` pays dividends every time you use AI for anything business-related.
