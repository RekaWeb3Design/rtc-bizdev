---
name: pitch-deck
description: Create a pitch deck or presentation for AI automation, agent workflow, or technology services. Use when the user asks for a presentation, deck, slides, or pitching materials. Auto-invoke for any slide-based deliverable. Produces a structured outline with speaker notes and optionally an HTML version.
---

# Pitch Deck Creation Skill

## When to Use
- Client presentation (in-person or screen share)
- Conference or event talk
- Internal stakeholder alignment
- Demo + value prop combined

## Slide Structure (Standard 10-Slide Deck)

### 1. Title Slide
- Company/service name
- Tagline (one sentence, outcome-focused)
- Date + presenter name

### 2. The Problem (1 slide)
- 2-3 bullet points MAX
- Use numbers if possible: "Finance teams spend 14 hours/week on manual reporting"
- Audience should feel this pain

### 3. The Solution (1 slide)
- "We do X so that Y can Z"
- One clear diagram or visual description
- No jargon — plain language

### 4. How It Works (1-2 slides)
- Step-by-step (3-5 steps)
- Can use: Before/After, or Process Flow
- Keep technical detail minimal; add to appendix if needed

### 5. Results / Proof (1 slide)
- 2-3 concrete outcomes: time saved, cost reduced, revenue increased
- Use anonymized client stories if needed: "A mid-size logistics company..."
- Avoid vague claims like "significant improvement"

### 6. Use Cases (1 slide)
- 3-4 industry-specific examples
- Format: [Industry] → [Problem] → [Outcome]

### 7. Why Now (1 slide)
- Market timing: why AI automation matters in 2025-2026
- 1-2 market stats
- Urgency without fear-mongering

### 8. Why Us (1 slide)
- Sign Coders' credentials
- Specific technical capability + business translation ability
- Keep humble and specific

### 9. Offer / Next Step (1 slide)
- What are we proposing right now?
- Options: Discovery call / Paid pilot / Partnership / Investment
- One clear CTA

### 10. Contact (1 slide)
- Name, email, LinkedIn
- Optional: QR code to a landing page

---

## Tone Per Audience

| Audience | Tone | Lead With |
|---|---|---|
| SME Owner | Practical, ROI-focused | Time/money saved |
| CTO/Tech Lead | Precise, architectural | How it works |
| Investor | Vision + traction | Market size + proof |
| Partner/Agency | Collaborative | Shared upside |

---

## Output Instructions

Every pitch deck produces **two deliverables** — never raw MD to clients.

### Step 1: Draft slide outline (internal only)
1. Produce a slide-by-slide outline with titles, bullet points, and speaker notes (internal draft)

### Step 2: HTML version (for screen-share / web link)
2. Use the `html-presentation` skill to produce a slide-by-slide HTML deck
3. Save to `outputs/reports/html/[client-slug]-pitchdeck-[date].html`
4. Format: full-screen slides, arrow key navigation, dark theme, max 30 words per slide

### Step 3: PDF version (for email attachment / print)
5. Use the `pdf-report` skill to produce a branded PDF with full slide content and speaker notes
6. Save to `outputs/reports/pdf/[client-slug]-pitchdeck-[date].pdf`
7. Format: A4, includes all detail and speaker notes for offline review

### Step 4: Update index
8. Update `outputs/files-index.json` with both HTML and PDF entries (no MD entries in the index)

---

## Prompt Examples (copy-paste ready)
```
Create a 10-slide pitch deck for [client type] in [industry]. 
Their main pain: [pain point]. I want to pitch [specific offer].
Audience: [who will see this]. Tone: [formal/casual/technical].
```

```
Turn this outline into a polished pitch deck. Add speaker notes.
Make it suitable for a 15-minute presentation.
```
