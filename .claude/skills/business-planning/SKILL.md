---
name: business-planning
description: Create business plan sections, financial models, go-to-market strategies, pricing frameworks, or strategic planning documents. Auto-invoke when user mentions business plan, GTM strategy, pricing model, unit economics, market analysis, competitive analysis, or strategic roadmap.
---

# Business Planning Skill

## Documents This Covers
- Full business plan sections
- Go-to-market (GTM) strategy
- Pricing framework
- Competitive landscape analysis
- Market sizing (TAM/SAM/SOM)
- Revenue model design
- Strategic roadmap

---

## Business Plan Sections (produce any subset on request)

### 1. Executive Summary
→ Use `investor-brief` skill if this is for investors
→ Use this skill for internal / operational planning version

### 2. Company Overview
- What Sign Coders does, for whom, since when
- Mission: one sentence
- Current stage: services → productizing

### 3. Market Analysis
**TAM/SAM/SOM Framework:**
- TAM: Total addressable market (e.g., global AI automation market)
- SAM: Serviceable — your geography + segment
- SOM: Realistically capturable in 3 years

**Sources to reference:**
- Gartner, McKinsey, Grand View Research for market size
- LinkedIn / industry reports for target company count

### 4. Problem & Solution
→ Reference `pitch-deck` skill structure

### 5. Product / Service Description
- Current: custom AI automation builds
- Near-term: productized service packages
- Long-term: SaaS / platform

**Service Package Template:**
| Tier | What's Included | Price | Timeline |
|---|---|---|---|
| Discovery | Workflow audit, automation map | €X | 2 weeks |
| Starter | 1 automation, full handover | €X | 4 weeks |
| Full Build | 3-5 automations, training | €X | 8 weeks |
| Retainer | Ongoing optimization + support | €X/mo | Ongoing |

### 6. Go-to-Market Strategy

**GTM Channels (rank by priority):**
1. Outbound (cold email + LinkedIn) — Anti's core channel
2. Referrals from existing clients
3. Partner network (agencies referring AI work)
4. Content (LinkedIn posts, case studies)
5. Events / speaking

**Target Customer Profile:**
- Company size: 20-500 employees
- Industries: logistics, finance, professional services, e-commerce
- Trigger: hiring freeze, scaling challenge, new digital initiative
- Decision maker: CEO/COO at SME, Head of Ops at mid-market

### 7. Competitive Analysis

**Framework: 2x2 Matrix**
- X axis: Technical depth (low → high)
- Y axis: Business focus (tool-centric → outcome-centric)
- Sign Coders positioning: high technical depth + high business focus

**Competitor types:**
- Big consultancies (Accenture AI) → expensive, slow, enterprise-only
- No-code platforms (Zapier, Make) → DIY, no implementation support
- Offshore dev shops → cheap but no AI expertise
- Local freelancers → limited scope, no strategic layer

**Sign Coders differentiator:** Senior AI expertise + business translation + local presence + speed

### 8. Financial Model

**Inputs to gather:**
- Current monthly revenue
- Average project value
- Average sales cycle (weeks)
- Monthly leads / pipeline
- Operating costs

**Output: 12-month projection table**

| Month | Leads | Closed | Revenue | Costs | Profit |
|---|---|---|---|---|---|
| 1 | | | | | |
| ... | | | | | |
| 12 | | | | | |

### 9. Operations & Team
- Current team structure
- Roles needed as you scale
- Delivery capacity (hours/projects per month)

### 10. Milestones & KPIs
- 30/60/90 day milestones
- 12-month revenue target
- Leading indicators: calls booked, proposals sent, close rate

---

## Pricing Framework

### Value-Based Pricing Formula
```
Price = (Annual value created for client) × 0.15–0.25
```
Example: Automation saves 20h/week × €50/h = €52,000/year → charge €8,000–€13,000

### Anchoring Strategy
Always present 3 tiers:
- **Lite** (they won't buy it, but it anchors the middle)
- **Standard** (this is what you want them to buy)
- **Premium** (for those who want everything)

---

## Output Instructions

Every business planning document produces **two deliverables** — never raw MD to clients.

1. Ask: which section(s) do you need?
2. Ask: is this for internal use, investors, or clients?
3. Draft content in Markdown (internal only)

### HTML version (for quick review / web sharing)
4. Use the `html-presentation` skill to produce a visual HTML summary
5. Save to `outputs/reports/html/[slug]-bizplan-[section]-[date].html`
6. Format: key highlights, charts, executive view

### PDF version (for detailed analysis / attachment)
7. Use the `pdf-report` skill to produce a branded, detailed PDF
8. Save to `outputs/reports/pdf/[slug]-bizplan-[section]-[date].pdf`
9. Format: A4, full analysis, data tables, financial models

### Update index
10. Update `outputs/files-index.json` with both HTML and PDF entries (no MD entries)

---

## Prompt Examples
```
Write a GTM strategy for Sign Coders targeting SMEs in [industry].
Main channel: outbound. Budget: low. Timeline: 6 months.
```

```
Build a pricing framework for AI automation services.
My average project takes 6 weeks. Target market: 50-200 person companies.
```

```
Create a competitive analysis for the AI automation market in [country/region].
My differentiator: speed + business focus + local.
```
