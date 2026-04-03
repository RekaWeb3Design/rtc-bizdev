---
name: html-presentation
description: Create a mini web presentation, HTML deck, visual landing page, or browser-based pitch. Auto-invoke when user asks for a web presentation, HTML version, visual link to share, browser-based deck, or anything that should open in a browser instead of a document.
---

> **Before generating any output, read `brand/brand.md` in full. Apply colors, typography, and tone rules automatically. Updated `brand/brand.md` always takes precedence.**

## Tagline Rule

Every output must include at least one approved RTC tagline as a visually distinct element — its own line, bold or italic, never buried in a sentence:

- *"Days NOT Months"* — primary, use in header or opening section
- *"We don't code anymore"* — for tech-aware audiences
- *"The Vapiano of Product Delivery"* — quality, affordable, scalable

Place the tagline on the title slide (Format B) or hero section (Format A).

## Offering Selector

Before generating output, confirm which offering applies:

| Signal | Offering |
|---|---|
| Invoice/workflow/ERP/CRM/Monday.com pain | **Workflow Automation Framework** |
| PoC, MVP, greenfield, legacy refactoring, custom build | **Orchestration System** |
| Training, upskilling, agentic AI learning | **AI Training** |

If ambiguous after reading the brief, ask one clarifying question before writing.

---

# HTML Presentation Skill

## What It Is
A single HTML file that works as a visual, shareable presentation. Open in any browser — no PowerPoint, no PDF viewer needed. Send as a file or host on a URL.

## Two Formats

### Format A: Scrollable Landing Page
- Reads top-to-bottom like a long sales page
- Great for: send-out, cold outreach, follow-up after a meeting
- Sections scroll smoothly
- Mobile-friendly

### Format B: Slide-by-Slide Deck
- Full-screen slides, navigate with arrow keys or buttons
- Great for: screen-share presentations, demo meetings
- Keyboard: `→` next, `←` back, `F` fullscreen

---

## Design Principles
- **One idea per screen** (Format B) or **one section per scroll block** (Format A)
- Dark mode by default (professional, easy on eyes in demos)
- Large numbers / stats as hero text
- Minimal copy — max 30 words per slide
- Accent color: pick one, use consistently

## HTML Template Variables
When building, confirm:
- `[primary_color]` — default: `#6366f1` (indigo)
- `[company_name]` — Roll the Code (default) or client-specific
- `[font_style]` — default: Inter (loaded from Google Fonts)
- `[format]` — scrollable or slide-deck

---

## Required Sections (Slide Deck)

```
Slide 1: Title + tagline
Slide 2: The problem (stat + one sentence)
Slide 3: The solution (visual or diagram)
Slide 4: How it works (3-step flow)
Slide 5: Results (numbers)
Slide 6: Use cases (3 tiles)
Slide 7: CTA (contact / book call)
```

## Required Sections (Scrollable)

```
Hero: Headline + subheadline + CTA button
Problem block: pain point with stat
Solution block: what you do
How it works: 3-step horizontal flow
Results: 3 metric cards
Social proof / mini case study
CTA block: book a call / contact
Footer: links
```

---

## Responsive Layout Rules (MANDATORY — apply to every HTML output)

Every HTML presentation must follow these rules without exception:

- All slide content must be horizontally centered: `max-width: 900px; margin: 0 auto;`
- Never left-align content without a centering wrapper
- Slides must be full-viewport-height: `min-height: 100vh; display: flex; align-items: center; justify-content: center;`
- Content container inside each slide: `max-width: 900px; width: 100%; margin: 0 auto; padding: 0 40px;`
- Never use fixed pixel widths on content blocks — use `max-width` + `width: 100%` instead
- Navigation controls must be fixed to bottom-center: `position: fixed; bottom: 32px; left: 50%; transform: translateX(-50%);`

---

## Technical Requirements
- **Single file** — all CSS and JS inline, no external dependencies except Google Fonts
- Fonts: `https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap`
- Works offline after first load (except fonts)
- No frameworks — vanilla HTML/CSS/JS only
- Smooth scroll: `scroll-behavior: smooth`
- Responsive: works on mobile (min-width: 320px)

---

## Output Instructions
1. Generate complete, ready-to-open HTML file
2. Save to `outputs/reports/html/[client-slug]-[type]-[date].html` per CLAUDE.md routing rules
3. Include comment at top: `<!-- Roll the Code | [date] | [format] -->`
4. Update `outputs/files-index.json` with the new HTML entry
5. Confirm: "Open this file in any browser. Works offline."

---

## Prompt Examples
```
Create an HTML scrollable landing page pitching AI workflow automation
to logistics companies. Primary color: blue. Include: problem, solution,
3 use cases, and a "Book a call" CTA.
```

```
Turn this pitch deck outline into an HTML slide-deck presentation.
Dark theme, slide-by-slide navigation, keyboard arrows.
```

```
Build a one-page visual summary of [topic] as an HTML file.
Keep it minimal — just the key numbers and a CTA.
```
