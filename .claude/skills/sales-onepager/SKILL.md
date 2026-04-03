---
name: sales-onepager
description: Create a sales one-pager or send-out document for Roll the Code's AI automation and product delivery services. Use when the user wants a kiküldős (sendable) document, one-pager, PDF-ready summary, email attachment, or short proposal. Auto-invoke for any single-page sales document. If the use case is ambiguous, ask one clarifying question before writing.
---

# Sales One-Pager Skill

## What It Is
A one-pager is a send-and-forget document. The reader opens it alone, without you explaining it. It must be:
- Self-contained (no "as discussed" without context)
- Skimmable in 30 seconds
- Actionable (one clear next step)

---

## Offering Selector

Before writing any one-pager, determine which Roll the Code offering fits the use case:

| Signal in the brief | Offering to feature |
|---|---|
| Invoice processing, workflow automation, ERP/CRM pain, Monday.com frustration, n8n, API integration | **Workflow Automation Framework** (n8n-based, lighter-touch, faster to sell) |
| PoC, MVP, greenfield product, legacy system refactoring, custom software build | **The Orchestration System** (flagship — agentic AI, architect-supervised, enterprise-grade) |
| Training inquiry, upskilling, agentic AI development learning | **AI Training** (door-opener, standalone or bundled) |

**Never mix the two main offerings in a single one-pager.** Pick one and commit. If the brief is ambiguous, default to whichever offering solves the stated pain point most directly. If the use case or target audience is ambiguous after reading the brief, ask one clarifying question before writing — do not guess.

---

## Tagline Rule

Every one-pager must include at least one of Roll the Code's approved taglines, treated as a proper tagline — not embedded lowercase in a sentence.

- *"Days NOT Months"* — primary, use in the header tagline or as a standalone emphasis line in Section 1 or Section 2
- *"We don't code anymore"* — provocative, good for tech-aware audiences
- *"The Vapiano of Product Delivery"* — quality, affordable, scalable

Correct usage: a dedicated line, bold or italic, visually distinct.
Incorrect usage: 'we deliver in days, not months' buried in a sentence.

---

## Structure (A4 or Letter, ~600-800 words)

### Header
- Logo / Name: Roll the Code
- Tagline: one outcome-focused sentence incorporating an approved tagline (see above)
- Optional: client's company name if personalized

### Section 1: The Situation (2-3 sentences)
What is happening in their world right now?
> "Mid-size companies in [industry] are losing [X hours/week] to [specific manual task]. As AI tools mature, the cost of not automating is rising."

### Section 2: What We Do (3-4 bullets)
- Specific. Not "AI solutions" — "We build automated invoice capture that matches POs and flags exceptions, cutting a 3-day cycle to same-day."
- Each bullet: capability → outcome
- Max 4 bullets
- Frame around the selected offering (see Offering Selector above)

### Section 3: Results (2-3 data points or mini-stories)
- Format: "[Company type] achieved [outcome] in [timeframe]"
- Anonymize client names unless approved
- If no real client data is available, do NOT invent specific percentages or ROI figures. Use outcome-directional language only: "operations teams typically reclaim significant admin hours" or "companies in this segment report faster supplier payment cycles" — never "70% reduction" or "ROI in 8 weeks" without a real, verified source.

### Section 4: How We Work Together
- 3-step process: Discovery → Build → Deploy
- Timeframes: "1 scoping call (45 min), build in days to weeks, milestone-based delivery"
- Low-commitment entry: "Start with a free 45-minute workflow audit"
- Pricing anchor where appropriate (€10K–€25K for focused builds, €50K–€200K for mid-size solutions)
- Fixed-scope, fixed-price — no open-ended retainers

### Section 5: Why Roll the Code
- Lead with: senior software architects who built an agentic AI orchestration system that delivers deterministic, production-grade results
- Make clear: this is not vibe coding — it is architect-supervised, enterprise-grade, and deployment-agnostic
- Position SignCoders as a cooperation partner (not a subcontractor, not "implementation capacity") — a social enterprise employing Deaf and hard-of-hearing professionals in mixed Deaf-hearing tech teams, adding both technical depth and a meaningful diversity story
- 1-2 sentences. Specific. Not "passionate team."

### Footer
- CTA: "Book a free 45-minute workflow audit" or "Reply to this email"
- Contact: antal@rollthecode.io | LinkedIn: /in/antalkarolyi
- rollthecode.io
- Optional: QR code

---

## Personalization Variables
When creating, ask or infer:
- `[industry]` — logistics, finance, HR, legal, e-commerce, etc.
- `[pain_point]` — what specific manual task are they doing?
- `[company_size]` — solo, SME (10-200), mid-market (200-1000)
- `[send_channel]` — email attachment, printed, LinkedIn DM

---

## Formatting Rules
- Use **bold** for key phrases only (max 5-6 per page)
- Short paragraphs: 2-3 sentences max
- Bullets over paragraphs in middle sections
- One visual element suggestion: a simple 3-step process diagram or before/after table
- The approved tagline must appear as a visually distinct element — its own line, bold or italic. Never inline within a sentence.

---

## Output Instructions
1. Produce the one-pager as a clean Markdown document
2. Include a note at the top: `<!-- Designed for [channel] — [date] -->`
3. Save to `outputs/sales/one-pagers/[client-slug]-onepager-[date].md`
4. After saving, update `outputs/files-index.json` as required by CLAUDE.md (include `content` field for MD files)
5. Offer to generate HTML version for web/email

---

## Prompt Examples
```
Write a sales one-pager for [industry] companies.
Pain point: [pain]. Offer: [specific service].
Send channel: email attachment.
```

```
Personalize this one-pager for [company name].
Context: [what you know about them].
Keep it under 700 words.
```
