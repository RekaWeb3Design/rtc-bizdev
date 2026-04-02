---
name: pdf-report
description: Generate branded PDF reports and documents for Roll the Code. Use when the user asks for a PDF, report, detailed document, printable version, or any deliverable that should be a multi-page branded PDF. Produces a puppeteer-optimized Markdown file and converts it to PDF.
---

# PDF Report Skill

## What It Is
A multi-page branded PDF document — more detailed and structured than a one-pager or HTML presentation. Designed for deep-dive deliverables: research reports, prospect briefs, market analyses, proposals, technical overviews, and investor packages.

The workflow: generate a puppeteer-optimized Markdown file with embedded HTML/CSS for branding, then convert to PDF via puppeteer.

---

## When to Use This (vs Other Skills)
| Need | Use |
|---|---|
| Quick send-out, email attachment (1 page) | `sales-onepager` |
| Browser-based visual deck | `html-presentation` |
| Slide outline for PowerPoint | `pitch-deck` |
| **Multi-page branded PDF document** | **`pdf-report`** (this skill) |

---

## Brand Requirements

**Always read `brand/brand.md` before generating.** Apply current colors, typography, and tone automatically.

### Current Brand Tokens (from brand.md)
- **Background:** `#0a0a0f` (near black)
- **Primary accent:** `#6366f1` (indigo)
- **Secondary accent:** `#818cf8` (bright indigo)
- **Text primary:** `#ffffff` (white)
- **Text secondary:** `#94a3b8` (light gray)
- **Card/surface:** `#12121a`
- **Border:** `#1e1e2e`
- **Font:** Inter (Google Fonts) — weights 400, 600, 700, 800

### Header Design
Every PDF starts with a dark branded header block:
- Background: `#0a0a0f`
- Left: text logo — **ROLL THE** `CODE` (CODE in `#6366f1`)
- Right: document date
- Below logo: document title in 28px Inter 800, white
- Below title: subtitle/tagline in 16px Inter 400, `#94a3b8`
- Bottom border: 3px solid `#6366f1`
- Padding: 40px horizontal, 30px vertical

### Footer Design
Every page includes a footer:
- Left: `Roll the Code — rollthecode.io`
- Right: page number
- Font: Inter 400, 10px, color `#94a3b8`
- Top border: 1px solid `#1e1e2e`

---

## Document Structure

### Required Elements (every PDF)
1. **Branded header** (as above)
2. **Executive summary** — 3-5 sentences, boxed in card background
3. **Body sections** — structured with clear H2/H3 hierarchy
4. **Data tables** — styled with alternating row colors and accent borders
5. **Key takeaways / recommendations** — highlighted box at the end
6. **Footer** with contact info and page numbers

### Optional Elements (use when relevant)
- Stat callout cards (large number + label, indigo left border)
- Comparison tables (competitor analysis, feature matrices)
- Timeline / milestone bars
- Quoted text blocks (testimonials, interview snippets)
- Source citations section

---

## Markdown-for-PDF Template

The output file is Markdown with an embedded `<style>` block at the top for puppeteer rendering. This is the structural template:

```markdown
<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800;900&display=swap');

@page {
  size: A4;
  margin: 25mm 20mm 25mm 20mm;
}

@media print {
  body { -webkit-print-color-adjust: exact; print-color-adjust: exact; }
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'Inter', sans-serif;
  font-size: 11pt;
  line-height: 1.6;
  color: #1a1a2e;
  background: #ffffff;
}

/* --- Header --- */
.pdf-header {
  background: #0a0a0f;
  color: #ffffff;
  padding: 30px 40px;
  margin: -25mm -20mm 30px -20mm;
  width: calc(100% + 40mm);
  border-bottom: 3px solid #6366f1;
  page-break-inside: avoid;
}
.pdf-header .logo {
  font-family: 'Inter', sans-serif;
  font-size: 14px;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 12px;
}
.pdf-header .logo span { color: #6366f1; }
.pdf-header .doc-title {
  font-size: 28px;
  font-weight: 800;
  line-height: 1.2;
  margin-bottom: 8px;
}
.pdf-header .doc-subtitle {
  font-size: 14px;
  font-weight: 400;
  color: #94a3b8;
}
.pdf-header .doc-date {
  font-size: 11px;
  color: #94a3b8;
  margin-top: 8px;
}

/* --- Executive Summary Box --- */
.exec-summary {
  background: #f0f0ff;
  border-left: 4px solid #6366f1;
  padding: 20px 24px;
  margin-bottom: 28px;
  border-radius: 0 6px 6px 0;
  page-break-inside: avoid;
}
.exec-summary h3 {
  font-size: 12pt;
  font-weight: 700;
  color: #6366f1;
  margin-bottom: 8px;
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* --- Section Headings --- */
h2 {
  font-size: 18pt;
  font-weight: 800;
  color: #0a0a0f;
  margin-top: 32px;
  margin-bottom: 12px;
  padding-bottom: 6px;
  border-bottom: 2px solid #6366f1;
}
h3 {
  font-size: 13pt;
  font-weight: 700;
  color: #1a1a2e;
  margin-top: 20px;
  margin-bottom: 8px;
}

/* --- Body --- */
p { margin-bottom: 10px; }
ul, ol { margin-bottom: 12px; padding-left: 20px; }
li { margin-bottom: 4px; }
strong { font-weight: 700; }

/* --- Tables --- */
table {
  width: 100%;
  border-collapse: collapse;
  margin: 16px 0 24px 0;
  font-size: 10pt;
}
th {
  background: #0a0a0f;
  color: #ffffff;
  font-weight: 700;
  text-align: left;
  padding: 10px 12px;
}
td {
  padding: 8px 12px;
  border-bottom: 1px solid #e2e2e2;
}
tr:nth-child(even) td { background: #f8f8fc; }

/* --- Stat Callout Card --- */
.stat-card {
  display: inline-block;
  border-left: 4px solid #6366f1;
  padding: 12px 20px;
  margin: 8px 16px 8px 0;
  background: #f8f8fc;
  page-break-inside: avoid;
}
.stat-card .stat-number {
  font-size: 28px;
  font-weight: 800;
  color: #6366f1;
  line-height: 1.1;
}
.stat-card .stat-label {
  font-size: 10px;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* --- Highlight / Takeaway Box --- */
.highlight-box {
  background: #0a0a0f;
  color: #ffffff;
  padding: 24px 28px;
  border-radius: 6px;
  margin: 24px 0;
  page-break-inside: avoid;
}
.highlight-box h3 {
  color: #6366f1;
  margin-top: 0;
}
.highlight-box p, .highlight-box li { color: #e2e8f0; }

/* --- Quote Block --- */
blockquote {
  border-left: 3px solid #818cf8;
  padding: 12px 20px;
  margin: 16px 0;
  font-style: italic;
  color: #475569;
  background: #fafaff;
}

/* --- Footer --- */
.pdf-footer {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  font-size: 9px;
  color: #94a3b8;
  border-top: 1px solid #1e1e2e;
  padding: 8px 20mm;
  display: flex;
  justify-content: space-between;
}

/* --- Page Break Utility --- */
.page-break { page-break-before: always; }
</style>

<div class="pdf-header">
  <div class="logo">ROLL THE <span>CODE</span></div>
  <div class="doc-title">[Document Title]</div>
  <div class="doc-subtitle">[Subtitle or tagline]</div>
  <div class="doc-date">[Date] · Confidential</div>
</div>

<div class="exec-summary">
  <h3>Executive Summary</h3>
  <p>[3-5 sentence summary of the document's key findings and recommendations.]</p>
</div>

## [Section 1 Title]

[Content here — paragraphs, bullets, tables, stat cards as needed.]

<div class="page-break"></div>

## [Section 2 Title]

[Continue with structured content.]

<div class="highlight-box">
  <h3>Key Takeaways</h3>
  <ul>
    <li>[Takeaway 1]</li>
    <li>[Takeaway 2]</li>
    <li>[Takeaway 3]</li>
  </ul>
</div>
```

---

## Content Guidelines

### Depth & Detail
PDF reports are the **most detailed** format in the toolkit. Unlike one-pagers (skimmable) or HTML decks (visual), PDFs are read carefully. Include:
- Full context and background
- Data with sources cited
- Analysis and reasoning, not just conclusions
- Specific recommendations with rationale
- Tables and structured comparisons where data supports it

### Writing Style
Follow `brand/brand.md` voice rules:
- **Confident, not arrogant** — state findings directly
- **Concrete, not vague** — specific numbers, dates, names (where approved)
- **Business-first** — lead sections with "so what" before the detail
- **Credibility through specificity** — cite sources, use real data

### Length
- **Short report:** 3-5 pages (prospect brief, meeting prep)
- **Standard report:** 6-12 pages (market research, proposal, analysis)
- **Deep dive:** 12-20 pages (investor package, technical assessment)

---

## PDF Conversion (Puppeteer)

After generating the `.md` file, convert to PDF using puppeteer:

```bash
node -e "
const puppeteer = require('puppeteer');
const fs = require('fs');
const { marked } = require('marked');

(async () => {
  const md = fs.readFileSync('INPUT_FILE.md', 'utf8');

  // Split style block from content
  const styleMatch = md.match(/<style>([\s\S]*?)<\/style>/);
  const style = styleMatch ? styleMatch[0] : '';
  const content = md.replace(/<style>[\s\S]*?<\/style>/, '');

  // Convert markdown portions to HTML (preserves raw HTML blocks)
  const html = marked.parse(content);

  const fullHtml = '<!DOCTYPE html><html><head><meta charset=\"utf-8\">' + style + '</head><body>' + html + '</body></html>';

  const browser = await puppeteer.launch({ headless: true, args: ['--no-sandbox'] });
  const page = await browser.newPage();
  await page.setContent(fullHtml, { waitUntil: 'networkidle0' });
  await page.pdf({
    path: 'OUTPUT_FILE.pdf',
    format: 'A4',
    printBackground: true,
    margin: { top: '25mm', bottom: '25mm', left: '20mm', right: '20mm' }
  });
  await browser.close();
  console.log('PDF generated successfully.');
})();
"
```

If puppeteer or marked are not installed, install them first:
```bash
npm install puppeteer marked
```

---

## Output Instructions

1. **Read `brand/brand.md`** before generating — apply current brand tokens
2. **Generate the Markdown file** with embedded styles, following the template above
3. **Save to:** `outputs/report-[topic]-[date].md`
4. **Convert to PDF:** `outputs/report-[topic]-[date].pdf` using the puppeteer script above
5. **Confirm to user:** file paths for both `.md` and `.pdf`

---

## Prompt Examples

```
Generate a PDF prospect brief for Barclays based on their legacy IT failures.
Include: background, the problem, why RTC is the right partner, proposed approach, pricing.
```

```
Create a PDF market research report on UK enterprise IT delivery failures.
Include data tables, sources, and recommendations for our sales team.
```

```
Turn this investor brief into a full branded PDF with detailed financials
and market analysis. 12-15 pages.
```

```
Generate a PDF version of our competitor analysis with a 2x2 positioning matrix.
```
