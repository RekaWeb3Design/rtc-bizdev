---
name: investor-brief
description: Generate investor decks, funding pitches, and executive summaries for Roll the Code. Auto-invoke when user mentions investors, funding, raise, valuation, investor deck, financial projections, or executive summary. Produces branded HTML + PDF with Pexels imagery.
---

> **Before generating any output, read `brand/brand.md` in full. Apply colors, typography, and tone rules automatically.**

## Tagline Rule

Every output must include at least one approved RTC tagline as a visually distinct element — its own line, bold or italic, never buried in a sentence:

- *"Days NOT Months"* — primary, use in header or opening section
- *"We don't code anymore"* — for tech-aware audiences
- *"The Vapiano of Product Delivery"* — quality, affordable, scalable

Place the tagline on the Title Page (Slide 1).

## Offering Overview

Investor materials cover the full company. When presenting the product, frame it around Roll the Code's three offerings and indicate which is the primary revenue driver:

| Offering | Description | Revenue role |
|---|---|---|
| **The Orchestration System** | Flagship. Agentic AI orchestration for PoC/MVP builds (€10K–€25K) and enterprise custom development (€50K–€200K). Architect-supervised, deterministic, deployment-agnostic. | Primary revenue driver |
| **Workflow Automation Framework** | n8n-based automation for ERP/CRM/workflow pain. Lighter-touch, faster to sell. | Fast entry point, recurring revenue potential |
| **AI Training** | Agentic AI development training. Door-opener, standalone or bundled. | Pipeline builder, brand positioning |

---

# Investor Brief Skill

## Brand Colors (Investor Override)

Investor materials use a darker, more premium palette:

| Role | Hex |
|---|---|
| Background | `#080A18` |
| Primary accent | `#5F5FFF` |
| Secondary accent | `#818cf8` |
| Text primary | `#ffffff` |
| Text secondary | `#94a3b8` |
| Card background | `#10122a` |
| Border | `#1a1c3a` |

---

## Mandatory Slide Order

This is the standard investor deck structure. Slides can be **shortened** (combining content) but **never reordered**. Omit a slide only if the user explicitly requests it.

| # | Slide | Purpose | Photo eligible? |
|---|---|---|---|
| 1 | **Title Page** | Company name, tagline, date, presenter | YES — full-bleed |
| 2 | **The Pain** | Market problem with data | YES — split or overlay |
| 3 | **Why Now? The Timing is Right** | Market timing, urgency, trends | YES — atmospheric |
| 4 | **The Team** | Board + Execution, Tech Lineup | NO |
| 5 | **Advisors and Partners** | Advisers, SignCoders, cooperation partners | NO |
| 6 | **Target Market** | Ideal customer profile, segments, geographies | YES — subtle overlay |
| 7 | **Market Opportunity** | TAM/SAM/SOM with data sources | YES — section divider |
| 8 | **Solution** | What we built, how it works, architecture | NO |
| 9 | **Traction & References** | Revenue, clients, proof points | NO |
| 10 | **Competitor Landscape** | 2x2 matrix or comparison table | NO |
| 11 | **Go To Market Strategy** | Channels, sales motion, partnerships | YES — atmospheric |
| 12 | **Business Model** | Pricing, margins, unit economics | NO |
| 13 | **Key Financials** | 3-year projections, burn rate | NO |
| 14 | **The Ask** | Raise amount, use of funds, milestones | YES — full-bleed |
| 15 | **Deep Dive Title Page** | Section divider for appendix content | YES — section divider |
| 16 | **Legal Framework** | Entity structure, IP ownership, terms | NO — clean background |
| 17 | **Market Research with Data** | Detailed TAM/SAM/SOM, sources, methodology | NO — data-heavy |

### Slide content rules

**Slide 1 — Title Page:**
- "ROLL THE CODE" (CODE in accent color)
- Primary tagline: *"Days NOT Months"*
- Subtitle: "Agentic AI Product Factory"
- Date + presenter name
- Full-bleed Pexels photo background

**Slide 2 — The Pain:**
- Lead with a stat: quantify the market pain
- Max 3 bullet points
- Audience should feel the problem viscerally

**Slide 3 — Why Now?**
- Market timing: why AI-orchestrated delivery is happening now
- 2-3 trend signals with data
- Window of opportunity: "6–9 months before early pioneers hit critical mass"

**Slide 4 — The Team:**
- Section heading: "Board of Directors & Execution"
- Always list in full: Antal Károlyi PhD, Réka Víg, Zoltán Héczei
- Tech Lineup separately: Gábor Tatár, Ákos Karacs, Roland Repka
- Advisers separately: Ágnes Szabó, Steve Balogh
- Never omit Antal, Réka, or Zoltán
- No stock photos — solid background, clean bios

**Slide 5 — Advisors and Partners:**
- SignCoders as cooperation partner (never subcontractor)
- Inflexion TrustChain, Szikra / TÉK / TnDtech, BusinessImpact.ai
- Position SignCoders diversity story as genuine differentiator

**Slide 6 — Target Market:**
- Ideal early adopter profile (4 criteria)
- 5 target segments with priority indicators
- Geographies: UK primary, Nordics, Hungary

**Slide 7 — Market Opportunity:**
- TAM/SAM/SOM numbers (if available, else note as TBD with methodology)
- Data sources cited
- Visual: concentric circles or bar chart

**Slide 8 — Solution:**
- The three offerings with clear hierarchy
- Orchestration System as flagship — explain: autonomous, orchestrated, deterministic
- "Not vibe coding" — architect-supervised
- Process flow or architecture diagram

**Slide 9 — Traction & References:**
- Current revenue / pipeline
- Client count + retention signals
- Growth rate or key milestones
- Use anonymized stories if clients not confirmed

**Slide 10 — Competitor Landscape:**
- 2x2 positioning matrix (AI capability vs. enterprise experience)
- Or comparison table: Large consultancies, No-code platforms, Young solopreneurs, Offshore dev shops
- RTC positioned in the "AI-first + senior team" quadrant

**Slide 11 — Go To Market:**
- Sales channels and motion
- Partnership strategy (Inflexion, Szikra network)
- Land-and-expand: workflow automation → orchestration → training

**Slide 12 — Business Model:**
- Pricing tiers: PoC €10K–€25K, Enterprise €50K–€200K
- Fixed-scope, milestone-based
- Margin structure
- Path from services to productized/recurring

**Slide 13 — Key Financials:**
- 3-year projection table (Clients, ARR, Revenue, COGS, Gross Margin, OpEx, EBITDA)
- State assumptions explicitly: ACV, sales cycle, churn, headcount

**Slide 14 — The Ask:**
- Raise amount
- Use of funds: 60% team, 30% sales funnel, 10% operations
- Key milestones this enables
- Full-bleed photo — forward-looking, aspirational

**Slide 15 — Deep Dive Title Page:**
- Section divider: "Appendix — Deep Dive"
- Full-bleed Pexels photo

**Slide 16 — Legal Framework:**
- Entity structure
- IP ownership
- Key terms and conditions
- Clean, text-heavy slide

**Slide 17 — Market Research with Data:**
- Detailed market sizing methodology
- Source citations
- Supporting data tables or charts

---

## Pexels Integration

Use the `pexels-images` skill for all photo-eligible slides:

1. Before generating HTML, fetch photos for slides marked "YES" in the table above
2. Use `curl -s -H "Authorization: $PEXELS_API_KEY"` to query Pexels API
3. Choose creative layouts per slide (full-bleed, split, overlay, divider)
4. Apply mandatory dark gradient veil over all photos
5. Add discreet photo credit (9px, 18% opacity, bottom-right)
6. If API fails, use fallback `background: #0D0F1E;`

### Suggested search queries per slide

| Slide | Query |
|---|---|
| Title Page | `technology abstract dark moody` |
| The Pain | `corporate office overwhelmed dark` |
| Why Now | `sunrise horizon future technology` |
| Target Market | `city skyline business district night` |
| Market Opportunity | `data visualization abstract blue` |
| Go To Market | `highway speed motion blur night` |
| The Ask | `handshake partnership business dark` |
| Deep Dive Title | `data center server room blue` |

---

## Tone for Investors

- **Traction beats vision** — lead with what's real
- **Acknowledge risks** — investors respect honesty; they're looking for awareness
- **Specific milestones** — "€500K ARR by Q4 2026" not "strong growth"
- **Crisp language** — no filler sentences
- **Urgency without panic** — the window is real, but we're prepared

---

## Document Types

This skill handles multiple investor document formats:

### 1. Investor Deck (primary — slides 1-17)
Full presentation following the mandatory slide order above.

### 2. Executive Summary (1-2 pages)
Condensed version: What we do → Market size → Traction → Business model → Team → The Ask.

### 3. Investment Memo (3-5 pages)
Prose document with sections: Company Overview, Problem & Market, Solution & Product, Business Model, Traction, Team, Use of Funds.

### 4. One-Line Pitch
For intros, LinkedIn, cold outreach.

---

## Financial Projection Template (3-Year)

| | Year 1 | Year 2 | Year 3 |
|---|---|---|---|
| Clients | X | Y | Z |
| ARR | €X | €Y | €Z |
| Revenue | | | |
| COGS | | | |
| Gross Margin | X% | Y% | Z% |
| OpEx | | | |
| EBITDA | | | |

**Assumptions to state explicitly:**
- Average contract value
- Sales cycle length
- Churn rate assumption
- Headcount plan

---

## Output Instructions

### Output location
Save all investor materials to `outputs/pitches/investors/`:
- `rtc-investor-deck-[date].html`
- `rtc-investor-deck-[date].pdf`
- For client-specific: `[client-slug]-investor-deck-[date].html`

### HTML version (for screen-share / web link)
1. Use `html-presentation` skill Format B (slide-by-slide deck)
2. Full-screen slides, arrow key navigation, keyboard shortcuts
3. Apply investor brand colors (`#080A18` background, `#5F5FFF` accent)
4. Pexels photos on eligible slides with dark veils
5. Save to `outputs/pitches/investors/`

### PDF version (for email attachment / deep-dive)
6. Use the `pdf-report` skill for branded PDF
7. Full detail including speaker notes, financials, team bios
8. Save to `outputs/pitches/investors/`

### Update index
9. Update `outputs/files-index.json` with both HTML and PDF entries

---

## Prompt Examples
```
Create an investor deck for Roll the Code.
We're raising €[amount]. Stage: pre-seed.
Current traction: [what we have].
```

```
Write a 2-page executive summary for investors.
Key message: AI automation services transitioning to productized delivery.
ARR: €[amount]. Raise: €[amount].
```

```
Build the full 17-slide investor deck with Pexels imagery.
Include all appendix slides.
```
