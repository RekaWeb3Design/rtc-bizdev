# Skills Audit — 2026-04-03

Audited all 7 skills in `.claude/skills/*/SKILL.md` against CLAUDE.md (source of truth) across 8 criteria: brand consistency, offering clarity, tagline compliance, data integrity, output path correctness, ambiguity handling, tone and voice, audience alignment.

---

## Summary

- **Total skills audited:** 7
- **Clean (no issues):** 1 (`sales-onepager`)
- **Minor issues (fix recommended):** 1 (`pdf-report`)
- **Major issues (fix required):** 5 (`html-presentation`, `pitch-deck`, `investor-brief`, `collaborator-deck`, `business-planning`)
- **High risk (fix before any use):** 0

---

## Per-Skill Results

---

### sales-onepager

**Status:** ✅ Clean

| Criterion | Result | Detail |
|---|---|---|
| Brand consistency | ✅ | Refers to "Roll the Code", correct contact (antal@rollthecode.io), SignCoders positioned as cooperation partner |
| Offering clarity | ✅ | Has an Offering Selector table covering all three RTC offerings with signal-based disambiguation |
| Tagline compliance | ✅ | Lists all three approved taglines, specifies visually distinct placement (own line, bold/italic) |
| Data integrity | ✅ | Explicitly forbids invented statistics: "do NOT invent specific percentages or ROI figures" |
| Output path | ✅ | Correct HTML + PDF dual-output workflow; paths match CLAUDE.md routing rules |
| Ambiguity handling | ✅ | "If the use case or target audience is ambiguous after reading the brief, ask one clarifying question before writing" |
| Tone and voice | ✅ | Matches CLAUDE.md: concrete, business-first, skimmable, avoids vague claims |
| Audience alignment | ✅ | Personalization variables for industry, pain point, company size, send channel |

**Required fixes:** None.
**Estimated effort:** N/A

---

### html-presentation

**Status:** 🔴 Major

| Criterion | Result | Detail |
|---|---|---|
| Brand consistency | ❌ | Line 36: `[company_name]` defaults to "Sign Coders" — must be "Roll the Code". Line 83: comment says "Anti Pitch Toolkit" — should be "Roll the Code" |
| Offering clarity | ❌ | No awareness of RTC's three offerings. Produces generic HTML with no offering context |
| Tagline compliance | ❌ | No mention of approved RTC taglines anywhere. Slide 1 says "Title + tagline" but doesn't reference the approved list |
| Data integrity | ✅ | Format skill — content is passed in from other skills; no data generation guidance needed |
| Output path | ❌ | Line 82: saves to `outputs/presentation-[topic]-[date].html` — should be `outputs/reports/html/[client-slug]-[type]-[date].html` per CLAUDE.md |
| Ambiguity handling | ✅ | Asks for format (scrollable vs slide-deck) and primary color |
| Tone and voice | ⚠️ | Minimal tone guidance. "Anti Pitch Toolkit" branding is stale. No reference to brand.md voice rules |
| Audience alignment | ❌ | No audience awareness. Doesn't know who the reader is or what they need to feel |

**Required fixes:**
1. Replace `Sign Coders` default in `[company_name]` with `Roll the Code` (line 36)
2. Replace `<!-- Anti Pitch Toolkit | [date] | [format] -->` with `<!-- Roll the Code | [date] | [format] -->` (line 83)
3. Add instruction: "Always read `brand/brand.md` before generating. Apply current brand tokens."
4. Add tagline rule: "Include at least one approved RTC tagline on the title slide/hero section, visually distinct"
5. Fix output path to `outputs/reports/html/[client-slug]-[type]-[date].html`
6. Add instruction to update `outputs/files-index.json` after saving
7. Add audience context reference to CLAUDE.md Audience Guide

**Estimated effort:** Minor (text replacements + 3 new paragraphs)

---

### pdf-report

**Status:** ⚠️ Minor

| Criterion | Result | Detail |
|---|---|---|
| Brand consistency | ✅ | Template uses "ROLL THE CODE" logo, rollthecode.io in footer. Correct branding throughout |
| Offering clarity | ✅ | Format skill — offering context comes from the calling skill. Appropriate for its role |
| Tagline compliance | ❌ | No mention of including an approved tagline in the document subtitle or header. Template has `[Subtitle or tagline]` placeholder but doesn't reference the approved list |
| Data integrity | ✅ | "Data with sources cited", "cite sources, use real data" — good guidance |
| Output path | ❌ | Line 375-376: saves to `outputs/report-[topic]-[date].md` and `outputs/report-[topic]-[date].pdf` — should be `outputs/reports/pdf/[client-slug]-[type]-[date].pdf`. Also saves a `.md` intermediate file with no instruction to treat it as draft-only |
| Ambiguity handling | ⚠️ | No explicit "ask before proceeding" instruction for unclear briefs |
| Tone and voice | ✅ | References brand/brand.md voice rules directly |
| Audience alignment | ⚠️ | Knows PDFs are "read carefully" but no specific audience mapping |

**Required fixes:**
1. Fix output path from `outputs/report-[topic]-[date].pdf` to `outputs/reports/pdf/[client-slug]-[type]-[date].pdf`
2. Mark the `.md` file as an internal draft: "The Markdown file is an intermediate build artifact — save to `outputs/drafts/` and do not include in `files-index.json`"
3. Add note: "Use an approved RTC tagline in the `[Subtitle or tagline]` header field when the document is client-facing"
4. Add instruction to update `outputs/files-index.json` with the PDF entry after conversion

**Estimated effort:** Trivial (path corrections + 2 sentences)

---

### pitch-deck

**Status:** 🔴 Major

| Criterion | Result | Detail |
|---|---|---|
| Brand consistency | ❌ | Line 51-53: "Sign Coders' credentials" — must be "Roll the Code". No mention of SignCoders as cooperation partner |
| Offering clarity | ❌ | No Offering Selector. Could produce a deck for any offering without knowing which one. No disambiguation logic |
| Tagline compliance | ❌ | Line 17: "Tagline (one sentence, outcome-focused)" — doesn't reference approved RTC taglines. No visually distinct placement rule |
| Data integrity | ✅ | Line 39: "Avoid vague claims like 'significant improvement'" — good |
| Output path | ✅ | Updated to correct HTML + PDF dual-output with proper paths |
| Ambiguity handling | ⚠️ | Asks for audience and tone but not which RTC offering to feature |
| Tone and voice | ✅ | Good tone-per-audience table (SME, CTO, Investor, Partner) |
| Audience alignment | ✅ | Clear audience-to-tone mapping |

**Required fixes:**
1. Replace "Sign Coders' credentials" (line 51-53) with "Roll the Code's credentials" and add SignCoders cooperation partner positioning
2. Add Offering Selector (copy from sales-onepager or adapt) so the deck knows which of the three offerings to feature
3. Add tagline rule: "Title slide must include one approved RTC tagline, visually distinct. Options: 'Days NOT Months', 'We don't code anymore', 'The Vapiano of Product Delivery'"
4. Add ambiguity handling: "If the brief doesn't specify which offering to pitch, ask before proceeding"

**Estimated effort:** Minor (1 rename + 2 new sections of ~5 lines each)

---

### investor-brief

**Status:** 🔴 Major

| Criterion | Result | Detail |
|---|---|---|
| Brand consistency | ❌ | Line 142: "executive summary for Sign Coders" — must be "Roll the Code". Line 28: "Anti's context" — should be "Antal's context" or "Founder context". No mention of SignCoders cooperation partner positioning |
| Offering clarity | ⚠️ | References "B2B AI automation services" generically (line 29). Doesn't map to the three defined RTC offerings or explain which to lead with for investors |
| Tagline compliance | ❌ | No mention of approved RTC taglines. Title slide / exec summary should carry one |
| Data integrity | ⚠️ | Financial projection template (lines 90-98) encourages filling in numbers with no warning about clearly labeling projections vs. actuals. Not high risk (investors expect projections) but should note: "Label all projections as estimates. State assumptions explicitly." |
| Output path | ✅ | Updated to correct HTML + PDF dual-output with proper paths |
| Ambiguity handling | ✅ | Asks document type, stage, and raise amount before proceeding |
| Tone and voice | ✅ | Strong: "Traction beats vision", "Acknowledge risks", "Specific milestones" |
| Audience alignment | ✅ | Clearly written for investors. Knows what they read in order |

**Required fixes:**
1. Replace all "Sign Coders" references with "Roll the Code" (lines 142, and any others in examples)
2. Replace "Anti's context" with "Founder context" or "Antal's context" (line 28)
3. Add tagline rule: "Include one approved RTC tagline on the title slide / exec summary header"
4. Add note to financial projections: "Label all figures as projections. State assumptions explicitly. Do not present estimates as actuals."
5. Add a brief offering overview: "When presenting the product, frame it around RTC's three offerings (Orchestration System, Workflow Automation, AI Training) and indicate which is the primary revenue driver"

**Estimated effort:** Minor (text replacements + 3 new sentences)

---

### collaborator-deck

**Status:** 🔴 Major

| Criterion | Result | Detail |
|---|---|---|
| Brand consistency | ❌ | 4 instances of "Sign Coders" that should be "Roll the Code": line 10 ("white-label Sign Coders' AI stack"), line 36 ("What Sign Coders Brings"), line 70 ("About Sign Coders"), line 107 ("partnership proposal for [specific company]"). SignCoders is not positioned as cooperation partner — it's used as the company name itself |
| Offering clarity | ⚠️ | Line 37: mentions "AI agents, workflow automation, rapid prototyping" but doesn't map to the three defined RTC offerings |
| Tagline compliance | ❌ | No mention of approved RTC taglines |
| Data integrity | ✅ | Partnership economics are presented as templates to fill in, not invented. Appropriate for this document type |
| Output path | ✅ | Updated to correct HTML + PDF dual-output with proper paths |
| Ambiguity handling | ✅ | Asks partnership model and partner profile before proceeding |
| Tone and voice | ✅ | Excellent peer-to-peer tone: "skip the hype", "be honest — it builds trust" |
| Audience alignment | ✅ | Clear: partners, not clients. Mutual framing throughout |

**Required fixes:**
1. Replace all "Sign Coders" with "Roll the Code" (4 instances: lines 10, 36, 70, and in examples)
2. Add SignCoders cooperation partner mention in Section 2 or "About" section: "Our cooperation partner SignCoders — a social enterprise employing Deaf and hard-of-hearing professionals in mixed Deaf-hearing tech teams — adds both technical depth and a meaningful diversity story"
3. Map capabilities to the three RTC offerings in Section 2
4. Add tagline rule: "Include one approved RTC tagline in the opportunity or title section"

**Estimated effort:** Minor (4 renames + 2 new paragraphs)

---

### business-planning

**Status:** 🔴 Major

| Criterion | Result | Detail |
|---|---|---|
| Brand consistency | ❌ | 6 instances of "Sign Coders" that should be "Roll the Code": lines 28, 76, 78, 84, 156, and section headers. Line 59: "Anti's core channel" — should be "Antal's" or "Founder's". No SignCoders cooperation partner positioning |
| Offering clarity | ⚠️ | Line 43-50: describes service tiers generically ("1 automation", "3-5 automations") without mapping to the three defined RTC offerings |
| Tagline compliance | ❌ | No mention of approved RTC taglines |
| Data integrity | ⚠️ | Financial model template (lines 96-101) and pricing framework (lines 118-121) encourage filling in projections with no warning about labeling estimates vs. actuals. Not high risk for internal planning docs but should note the distinction |
| Output path | ✅ | Updated to correct HTML + PDF dual-output with proper paths |
| Ambiguity handling | ✅ | Asks which sections, audience (internal/investors/clients) |
| Tone and voice | ⚠️ | Uses informal "Anti" (line 59) instead of "Antal". Otherwise functional but lacks explicit reference to brand.md voice rules |
| Audience alignment | ✅ | Distinguishes internal vs. investor vs. client use |

**Required fixes:**
1. Replace all "Sign Coders" with "Roll the Code" (6 instances)
2. Replace "Anti's" with "Antal's" (line 59)
3. Add SignCoders cooperation partner mention in Company Overview section
4. Map the Product/Service Description to the three defined RTC offerings (Orchestration System, Workflow Automation Framework, AI Training)
5. Add tagline rule: "Include one approved RTC tagline in the Executive Summary or Company Overview"
6. Add note: "Always read `brand/brand.md` before generating. Apply current voice and tone rules."
7. Add to financial sections: "Label all projections as estimates. State assumptions explicitly."

**Estimated effort:** Minor (6 renames + 4 new paragraphs)

---

## Recommended Fix Order

Priority order: most impactful fixes first. All are Major except #6.

| # | Skill | Most Important Fix | Effort |
|---|---|---|---|
| 1 | `html-presentation` | Replace "Sign Coders" default, fix output path, add brand.md reference — this skill is called by every other skill for HTML output, so errors here propagate everywhere | Minor |
| 2 | `pitch-deck` | Replace "Sign Coders", add Offering Selector and tagline rule — client-facing, high visibility | Minor |
| 3 | `collaborator-deck` | Replace 4x "Sign Coders" with "Roll the Code", add SignCoders partner positioning | Minor |
| 4 | `investor-brief` | Replace "Sign Coders" in examples, fix "Anti's", add tagline rule — investor-facing, trust-critical | Minor |
| 5 | `business-planning` | Replace 6x "Sign Coders", fix "Anti's", map offerings to three RTC pillars | Minor |
| 6 | `pdf-report` | Fix output path, mark MD as draft-only, add tagline reference — format skill, lower content risk | Trivial |

---

## Cross-Cutting Patterns

Three systemic issues appear across most skills:

1. **"Sign Coders" naming (5 of 7 skills):** The original skills were written before the "Roll the Code" brand was established. A bulk find-and-replace of "Sign Coders" → "Roll the Code" across all SKILL.md files would fix the majority of brand consistency issues in one pass.

2. **No tagline enforcement (6 of 7 skills):** Only `sales-onepager` has the tagline rule. The same block should be added to all content-producing skills (pitch-deck, investor-brief, collaborator-deck, business-planning) and the format skills should reference it (html-presentation header/hero, pdf-report subtitle).

3. **No Offering Selector (5 of 7 skills):** Only `sales-onepager` has an Offering Selector. The `pitch-deck`, `investor-brief`, `collaborator-deck`, and `business-planning` skills all produce output that should be framed around a specific RTC offering but have no disambiguation logic. A shared offering selector block could be extracted and referenced.

---

*Audit completed 2026-04-03 by Claude. Source of truth: CLAUDE.md + brand/brand.md.*
