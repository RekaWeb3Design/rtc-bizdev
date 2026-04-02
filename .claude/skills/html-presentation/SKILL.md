---
name: html-presentation
description: Create a mini web presentation, HTML deck, visual landing page, or browser-based pitch. Auto-invoke when user asks for a web presentation, HTML version, visual link to share, browser-based deck, or anything that should open in a browser instead of a document.
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
- `[company_name]` — Sign Coders or client-specific
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
2. Save to `/outputs/presentation-[topic]-[date].html`
3. Include comment at top: `<!-- Anti Pitch Toolkit | [date] | [format] -->`
4. Confirm: "Open this file in any browser. Works offline."

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
