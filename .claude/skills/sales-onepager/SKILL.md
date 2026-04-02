---
name: sales-onepager
description: Create a sales one-pager or send-out document for AI automation services. Use when the user wants a kiküldős (sendable) document, one-pager, PDF-ready summary, email attachment, or short proposal. Auto-invoke for any single-page sales document.
---

# Sales One-Pager Skill

## What It Is
A one-pager is a send-and-forget document. The reader opens it alone, without you explaining it. It must be:
- Self-contained (no "as discussed" without context)
- Skimmable in 30 seconds
- Actionable (one clear next step)

## Structure (A4 or Letter, ~600-800 words)

### Header
- Logo / Name: Sign Coders
- Tagline: one outcome-focused sentence
- Optional: client's company name if personalized

### Section 1: The Situation (2-3 sentences)
What is happening in their world right now?
> "Mid-size companies in [industry] are losing [X hours/week] to [specific manual task]. As AI tools mature, the cost of not automating is rising."

### Section 2: What We Do (3-4 bullets)
- Specific. Not "AI solutions" — "We build automated lead qualification flows that route hot leads to sales reps within 5 minutes."
- Each bullet: capability → outcome
- Max 4 bullets

### Section 3: Results (2-3 data points or mini-stories)
- Format: "[Company type] achieved [outcome] in [timeframe]"
- Anonymize client names unless approved
- If no data yet: use plausible estimates with "typical clients see..."

### Section 4: How We Work Together
- 3-step process: Discovery → Build → Deploy
- Timeframes: "2-week discovery, 4-6 week build, 1-week handover"
- Low-commitment entry: "Start with a free 45-minute workflow audit"

### Section 5: Why Sign Coders
- 1-2 sentences. Specific. Not "passionate team."
- Example: "We've automated workflows for companies in logistics, finance, and professional services — with live systems running in under 6 weeks."

### Footer
- CTA: "Book a 30-minute call: [link]" or "Reply to this email"
- Contact: email + LinkedIn
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

---

## Output Instructions
1. Produce the one-pager as a clean Markdown document
2. Include a note at the top: "// Designed for [channel] — [date]"
3. Save to `/outputs/onepager-[client/topic]-[date].md`
4. Offer to generate HTML version for web/email

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
