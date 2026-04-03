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

.tagline-block {
  background: #0a0a0f;
  color: #6366f1;
  font-size: 18pt;
  font-weight: 800;
  text-align: center;
  padding: 18px 24px;
  border-radius: 6px;
  margin-bottom: 24px;
  letter-spacing: 0.02em;
  page-break-inside: avoid;
}

h2 {
  font-size: 16pt;
  font-weight: 800;
  color: #0a0a0f;
  margin-top: 28px;
  margin-bottom: 10px;
  padding-bottom: 6px;
  border-bottom: 2px solid #6366f1;
}
h3 {
  font-size: 12pt;
  font-weight: 700;
  color: #1a1a2e;
  margin-top: 16px;
  margin-bottom: 6px;
}

p { margin-bottom: 10px; }
ul, ol { margin-bottom: 12px; padding-left: 20px; }
li { margin-bottom: 5px; }
strong { font-weight: 700; }

table {
  width: 100%;
  border-collapse: collapse;
  margin: 16px 0 20px 0;
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

.process-table {
  width: 100%;
  border-collapse: collapse;
  margin: 16px 0;
}
.process-table td {
  padding: 12px 16px;
  border: 1px solid #e2e2e2;
  vertical-align: top;
  font-size: 10pt;
}
.process-table .phase-head {
  background: #6366f1;
  color: #ffffff;
  font-weight: 700;
  font-size: 10pt;
  padding: 10px 16px;
  text-align: center;
}
.process-table .phase-time {
  font-size: 9pt;
  color: #6366f1;
  font-weight: 700;
  display: block;
  margin-top: 6px;
}

blockquote {
  border-left: 3px solid #818cf8;
  padding: 12px 20px;
  margin: 16px 0;
  font-style: italic;
  color: #475569;
  background: #fafaff;
}

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
  background: #ffffff;
}

.page-break { page-break-before: always; }
</style>

<div class="pdf-footer">
  <span>Roll the Code — rollthecode.io</span>
  <span>Confidential · April 2026</span>
</div>

<div class="pdf-header">
  <div class="logo">ROLL THE <span>CODE</span></div>
  <div class="doc-title">Legacy Core Banking Modernisation</div>
  <div class="doc-subtitle">"Days NOT Months" — A One-Pager for UK Fintech CTOs</div>
  <div class="doc-date">April 2026 · Confidential · Prepared by Roll the Code</div>
</div>

<div class="tagline-block">"Days NOT Months"</div>

<div class="exec-summary">
  <h3>Executive Summary</h3>
  <p>Mid-size UK fintechs are losing engineering velocity to legacy core banking systems that take 18 months to update. Roll the Code's flagship Orchestration System reverses this: we apply architect-supervised, multi-layered agentic AI to reverse-engineer your legacy codebase, produce a validated modern specification, and deliver a production-ready replacement in weeks — not months. Deterministic results. Fixed price. No lock-in. Start with one non-critical module and expand with confidence.</p>
</div>

## The Situation

Your legacy core banking system is not the problem. The 18-month update cycle is.

Mid-size UK fintechs are caught between regulators demanding faster change and legacy architectures that make change brutally expensive. Every sprint against a monolithic core burns engineering capacity, delays product roadmaps, and compounds technical debt. The firms that modernise first — in 2026 — will carry the architectural advantage for the next decade.

<div class="stat-card">
  <div class="stat-number">18mo</div>
  <div class="stat-label">Avg. time to update a core banking module</div>
</div>
<div class="stat-card">
  <div class="stat-number">60–70%</div>
  <div class="stat-label">Engineering capacity lost to legacy maintenance</div>
</div>
<div class="stat-card">
  <div class="stat-number">6–9mo</div>
  <div class="stat-label">Window before early movers pull ahead</div>
</div>

## What We Do

We apply our flagship **Orchestration System** to reverse-engineer, specify, and rebuild legacy banking components at speed.

- **Reverse-engineer your legacy system** — AI pipeline reads your existing codebase and produces a clean, modern technical specification. Static analysis, dependency mapping, behaviour extraction — in days.
- **Generate a validated replacement** — deterministic, architect-supervised AI implementation. Not vibe coding. Not a prototype. Production-grade output against the validated spec.
- **Deploy to your stack** — tech-stack agnostic, deployment agnostic. Your infrastructure, your compliance boundaries, your rules.
- **Start non-critical, expand with confidence** — begin with a self-contained module to prove the approach internally before touching mission-critical rails.

> *"Days NOT Months"* — a module that would take your team 18 months to refactor is deliverable in weeks.

## Results

| Scenario | Legacy Situation | RTC Outcome |
|---|---|---|
| Reporting module | 6-month internal project | Delivered in under 4 weeks |
| Enterprise integration | Stalled 12+ months | Unblocked by reverse-engineering spec in days |
| Discovery-to-spec | Months of architectural archaeology | Reduced to days across multiple engagements |

*Client names withheld. Available under NDA on request.*

## How We Work Together

<table class="process-table">
  <tr>
    <td class="phase-head">Step 1<br>Scoping Call</td>
    <td class="phase-head">Step 2<br>Build</td>
    <td class="phase-head">Step 3<br>Deploy &amp; Hand Over</td>
  </tr>
  <tr>
    <td>45 minutes. Map the target module, assess codebase complexity, define fixed scope. Clear timeline and price. No open-ended engagement.<span class="phase-time">45 Minutes</span></td>
    <td>Orchestration pipeline executes reverse engineering, spec generation, and implementation. Senior architects supervise every milestone. You approve before we proceed.<span class="phase-time">Days to Weeks</span></td>
    <td>Production-ready code, documented and tested. Deployed to your infrastructure. Full handover to your team. No retainer, no lock-in.<span class="phase-time">Your Infrastructure</span></td>
  </tr>
</table>

**Pricing:** €50K–€200K for mid-size non-critical solutions. Fixed scope, fixed price. Proposal within 5 working days of scoping call.

<div class="page-break"></div>

## Why Roll the Code

Our Orchestration System was built by software architects with decades of enterprise delivery experience:

- **Gábor Tatár** — AI orchestration product owner, software architect, 20+ years enterprise delivery
- **Ákos Karacs** — QA, business analyst, software architect; built the determinism layer of our pipeline
- **Roland Repka** — senior full-stack developer, production delivery
- **Steve Balogh** — enterprise IT adviser

**SignCoders** is our cooperation partner — a social enterprise employing Deaf and hard-of-hearing professionals in mixed Deaf–hearing tech teams — for agentic AI implementation and UX/UI. They add genuine technical depth and a diversity story that resonates with enterprise procurement. Not a subcontractor. A partner.

This is not a thin AI wrapper over a code generator. It is a multi-layered, deployment-agnostic, agentic AI pipeline that produces deterministic, production-grade results — because software architects, not prompt engineers, designed it.

## Use Cases for UK Fintech

| Module | Legacy Pain | RTC Outcome |
|---|---|---|
| Reporting &amp; analytics layer | Manual extraction, stale data, core DB coupling | Modern API-connected reporting — weeks |
| Onboarding &amp; KYC workflow | 3rd-party dependencies, compliance drift | Clean reimplementation — spec + build |
| Payment reconciliation | Monolithic logic, untestable edge cases | Modular, testable replacement |

<div class="highlight-box">
  <h3>Key Takeaways</h3>
  <ul>
    <li>Your 18-month update cycle is a delivery problem, not an architecture problem — and it is solvable now</li>
    <li>We reverse-engineer, specify, and rebuild legacy modules in weeks using deterministic, architect-supervised AI orchestration</li>
    <li>Start with one non-critical module at a fixed price — prove it, then expand</li>
    <li>The window is 6–9 months before early movers in AI-assisted modernisation have pulled decisively ahead</li>
    <li>One 45-minute scoping call. A fixed-scope proposal within 5 working days. No risk to start.</li>
  </ul>
</div>

**Book a 45-minute scoping call:**
antal@rollthecode.io | rollthecode.io | LinkedIn: /in/antalkarolyi
