# Skills Sync Report — 2026-04-03

## Source changes detected

- **CLAUDE.md:** Team section renamed from "Board of Directors" to "Board of Directors & Execution". Réka Víg role updated from "AI enthusiast, UX/UI designer, serial entrepreneur, AI-first approach" to "AI-first product strategist, UX/UI designer, serial entrepreneur". Gábor Tatár moved before Ákos Karacs in Tech Lineup. Advisers expanded from inline list to full-line entries (Ágnes Szabó — branding and marketing; Steve Balogh — enterprise IT). New "Important rules for all documents" section added specifying team listing order, section heading, completeness rules, and SignCoders framing.

- **brand/brand.md:** No changes since last sync.

---

## Skills updated

| Skill | What changed | Reason |
|---|---|---|
| `sales-onepager` | Added `brand/brand.md` read instruction at top of file | Instruction was missing; all visual-output skills must read brand/brand.md per CLAUDE.md |
| `pitch-deck` | Added team listing rules block to Slide 8 "Why Us" guidance | CLAUDE.md now has explicit "Important rules for all documents" specifying section heading, full Board & Execution listing, Tech Lineup order (Gábor before Ákos), expanded Adviser entries, and Réka's updated role title |
| `investor-brief` | Added team listing rules block to Section 6 "Team" guidance | Same reason — team structure and role titles must be correct in investor documents where team bios are most prominent |
| `collaborator-deck` | Added team listing rules block to Section 8 "About Roll the Code" guidance | Same reason — partner-facing documents name the team and must reflect current structure |
| `business-planning` | Added team listing rules block to Section 9 "Operations & Team" guidance | Same reason — business plans include team sections and must apply the new listing rules |

---

## Skills unchanged

| Skill | Status |
|---|---|
| `html-presentation` | In sync — brand read instruction present, no team content, taglines and offering selector current |
| `pdf-report` | In sync — brand read instruction present, no team content, brand tokens match brand/brand.md, tagline rule present |

---

## Notes

The team listing rules block added to `pitch-deck`, `investor-brief`, `collaborator-deck`, and `business-planning` is a verbatim encoding of the new CLAUDE.md "Important rules for all documents" section. It is placed directly in the relevant team-facing section of each skill so the rule fires at the point of content generation, not as a generic header note.

`sales-onepager` did not require team listing rules (it does not produce a team section) but did require the brand read instruction which was the only skill missing it.
