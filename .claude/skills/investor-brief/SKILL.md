---
name: investor-brief
description: Create investor materials, funding pitch documents, executive summaries for investors, or business planning documents with financial framing. Auto-invoke when user mentions investors, funding, raise, valuation, business plan, financial projections, or executive summary.
---

> **Before generating any output, read `brand/brand.md` in full. Apply colors, typography, and tone rules automatically. Updated `brand/brand.md` always takes precedence.**

## Tagline Rule

Every output must include at least one approved RTC tagline as a visually distinct element — its own line, bold or italic, never buried in a sentence:

- *"Days NOT Months"* — primary, use in header or opening section
- *"We don't code anymore"* — for tech-aware audiences
- *"The Vapiano of Product Delivery"* — quality, affordable, scalable

Place the tagline on the title slide (decks) or executive summary header (memos).

## Offering Overview

Investor materials cover the full company. When presenting the product, frame it around Roll the Code's three offerings and indicate which is the primary revenue driver:

| Offering | Description | Revenue role |
|---|---|---|
| **The Orchestration System** | Flagship. Agentic AI orchestration for PoC/MVP builds (€10K–€25K) and enterprise custom development (€50K–€200K). Architect-supervised, deterministic, deployment-agnostic. | Primary revenue driver |
| **Workflow Automation Framework** | n8n-based automation for ERP/CRM/workflow pain. Lighter-touch, faster to sell. | Fast entry point, recurring revenue potential |
| **AI Training** | Agentic AI development training. Door-opener, standalone or bundled. | Pipeline builder, brand positioning |

---

# Investor Brief Skill

## Document Types This Covers
1. **Executive Summary** (1-2 pages) — email-first teaser
2. **Investor Deck** (10-12 slides) — meeting presentation
3. **Investment Memo** (3-5 pages) — detailed written document
4. **One-Line Pitch** — for intros, LinkedIn, cold outreach

---

## Executive Summary Structure (1-2 pages)

**What investors read in order:**
1. What you do (1 sentence)
2. Market size (TAM/SAM/SOM)
3. Traction / proof (even early signals count)
4. Business model (how you make money)
5. Team (why you)
6. Ask (how much, for what)

**Founder context to weave in:**
- B2B AI automation services → productizing into SaaS
- Revenue from custom builds → transition to recurring
- Technical founder with commercial experience
- Existing clients = proof of demand

---

## Investor Deck Structure (12 slides)

1. Title + tagline
2. Problem — with market pain framing
3. Solution — "the wedge" (what you start with)
4. Market size — TAM/SAM/SOM with source
5. Business model — pricing, margins, LTV
6. Traction — revenue, clients, MoM growth
7. Product / Demo — screenshots or live demo
8. Go-to-market — how you get clients
9. Competition — 2x2 matrix or table
10. Team — bios with relevant credentials
11. Financials — 3-year projections (revenue, costs, burn)
12. The Ask — amount, use of funds, milestones

---

## Investment Memo Structure (prose document)

### Section 1: Company Overview (½ page)
What, for whom, why now

### Section 2: Problem & Market (1 page)
- Quantify the pain
- Market size with sources
- Trends accelerating the need

### Section 3: Solution & Product (1 page)
- What you've built
- How it works (simplified)
- What makes it defensible (IP, network effect, switching cost)

### Section 4: Business Model (½ page)
- Revenue streams
- Unit economics (CAC, LTV, gross margin)
- Path to profitability

### Section 5: Traction (½ page)
- Current revenue / ARR
- Clients + retention
- Growth rate

### Section 6: Team (½ page)
- Why this team
- Relevant experience
- Gaps and how you fill them

### Section 7: Use of Funds (½ page)
- How much you're raising
- Allocation: product / sales / ops
- Key milestones this enables

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

## Tone for Investors
- **Traction beats vision** — lead with what's real
- **Acknowledge risks** — investors respect honesty; they're looking for awareness
- **Specific milestones** — "€500K ARR by Q4 2026" not "strong growth"
- **Crisp language** — no filler sentences

---

## Output Instructions

Every investor document produces **two deliverables** — never raw MD to clients.

1. Ask: document type? (exec summary / deck / memo)
2. Ask: stage? (pre-revenue / early traction / scaling)
3. Ask: raise amount + use of funds?
4. Draft content in Markdown (internal only)

### HTML version (for web sharing / quick review)
5. Use the `html-presentation` skill to produce a visual HTML version
6. Save to `outputs/reports/html/[client-slug]-investor-[type]-[date].html`
7. Format: executive-level, skimmable, key metrics as hero text

### PDF version (for email attachment / deep-dive)
8. Use the `pdf-report` skill to produce a branded, detailed PDF
9. Save to `outputs/reports/pdf/[client-slug]-investor-[type]-[date].pdf`
10. Format: full detail, financials, team bios, market data

### Update index
11. Update `outputs/files-index.json` with both HTML and PDF entries (no MD entries)

---

## Prompt Examples
```
Write a 2-page executive summary for Roll the Code.
We're raising €[amount]. Current ARR: €[amount].
Main pitch: AI automation services transitioning to SaaS.
```

```
Build an investor deck outline for [company/product].
Stage: [pre-seed/seed/series A].
Key traction: [what you have].
```
