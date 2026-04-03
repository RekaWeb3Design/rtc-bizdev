---
name: collaborator-deck
description: Create a partnership pitch, collaborator deck, or co-builder proposal. Auto-invoke when user mentions finding partners, collaborators, agencies, co-founders, joint ventures, white-label partnerships, or revenue-sharing arrangements.
---

# Collaborator / Partner Deck Skill

## Who This Is For
Not clients, not investors — **potential co-builders and partners:**
- Development agencies who could white-label Sign Coders' AI stack
- Consultants who need an AI implementation partner
- Industry specialists (logistics, finance, legal) who bring domain + we bring AI
- Freelancers or boutique studios for project collaboration

---

## What Makes This Different From a Sales Deck

| Sales Deck | Collaborator Deck |
|---|---|
| "Here's what we can do for you" | "Here's what we can build together" |
| Client pays | Revenue is shared |
| One-directional | Partnership is mutual |
| Lead with their pain | Lead with shared upside |

---

## Structure (8-10 slides or sections)

### 1. The Opportunity (not "the problem")
- Market-level: "AI automation is a €50B market growing 35% YoY"
- The gap: "Most businesses need it but don't know how to buy it"
- Our position in it

### 2. What Sign Coders Brings
- Technical capabilities (AI agents, workflow automation, rapid prototyping)
- Existing clients / pipeline
- Track record: delivery speed, tech stack

### 3. What We're Looking For In a Partner
- Be specific: domain expertise, client base, geographic reach, or delivery capacity
- What kind of partner thrives here?
- What kind doesn't fit (be honest — it builds trust)

### 4. How We Work Together
- Model options:
  - **Referral** — you refer, we deliver, you earn X%
  - **White-label** — you sell, we build, your brand
  - **Co-delivery** — joint team on joint projects
  - **Product co-founder** — equity + effort based
- Be clear which model you're proposing in this specific deck

### 5. Economics (the honest slide)
- Revenue split / fee structure
- Who owns the client relationship?
- Who handles support?
- IP ownership
- Be direct — partners respect transparency

### 6. Sample Project / Case Study
- A project that would have been better with a partner
- What role they would have played
- What the outcome could have been

### 7. What a First Step Looks Like
- Low commitment: "Let's do one project together"
- Or: "30-min call to see if there's a fit"
- No pressure framing

### 8. About Sign Coders
- 3-4 sentences. Specific. Real.

---

## Tone
- **Peer-to-peer** — not selling down, not pitching up
- **Honest about what you need** — strength, not weakness
- **Win-win framing throughout** — "here's what's in it for both of us"
- Skip the hype — developers and agencies are immune to buzzwords

---

## Output Instructions

Every collaborator deck produces **two deliverables** — never raw MD to clients.

1. Ask: partnership model? (referral / white-label / co-delivery / co-founder)
2. Ask: partner profile? (agency, consultant, specialist, freelancer)
3. Draft content in Markdown (internal only)

### HTML version (for web sharing / intro link)
4. Use the `html-presentation` skill to produce a visual HTML deck
5. Save to `outputs/reports/html/[client-slug]-collab-deck-[date].html`
6. Format: peer-to-peer tone, visual, shareable link

### PDF version (for email attachment / formal proposal)
7. Use the `pdf-report` skill to produce a branded PDF with full terms and economics
8. Save to `outputs/reports/pdf/[client-slug]-collab-deck-[date].pdf`
9. Format: A4, detailed partnership terms, revenue model, case studies

### Update index
10. Update `outputs/files-index.json` with both HTML and PDF entries (no MD entries)

---

## Prompt Examples
```
Create a collaborator deck for digital agencies who don't have
AI capabilities in-house but have clients asking for automation.
Model: white-label. We build, they sell.
```

```
Write a partnership proposal for [specific company / type].
We want to co-deliver AI automation projects in [industry].
Revenue split: 60/40 (we build, they bring clients).
```
