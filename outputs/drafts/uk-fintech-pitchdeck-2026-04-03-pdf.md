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

.slide-section {
  page-break-inside: avoid;
  margin-bottom: 32px;
  padding-bottom: 24px;
  border-bottom: 1px solid #e2e2e2;
}
.slide-section:last-of-type { border-bottom: none; }

.slide-number {
  display: inline-block;
  background: #6366f1;
  color: #ffffff;
  font-size: 9pt;
  font-weight: 700;
  padding: 3px 10px;
  border-radius: 100px;
  letter-spacing: 1px;
  text-transform: uppercase;
  margin-bottom: 10px;
}

.slide-label {
  font-size: 9pt;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: #6366f1;
  margin-bottom: 8px;
  display: block;
}

h2 {
  font-size: 16pt;
  font-weight: 800;
  color: #0a0a0f;
  margin-top: 8px;
  margin-bottom: 12px;
  padding-bottom: 6px;
  border-bottom: 2px solid #6366f1;
}
h3 {
  font-size: 12pt;
  font-weight: 700;
  color: #1a1a2e;
  margin-top: 14px;
  margin-bottom: 6px;
}
h4 {
  font-size: 10pt;
  font-weight: 700;
  color: #6366f1;
  margin-top: 10px;
  margin-bottom: 4px;
  text-transform: uppercase;
  letter-spacing: 1px;
}

p { margin-bottom: 10px; }
ul, ol { margin-bottom: 12px; padding-left: 20px; }
li { margin-bottom: 5px; }
strong { font-weight: 700; }

.speaker-notes {
  background: #f8f8fc;
  border-left: 3px solid #818cf8;
  padding: 12px 16px;
  margin-top: 12px;
  font-size: 9.5pt;
  color: #475569;
  font-style: italic;
  border-radius: 0 4px 4px 0;
}
.speaker-notes strong { color: #1a1a2e; font-style: normal; }

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
  vertical-align: top;
}
tr:nth-child(even) td { background: #f8f8fc; }

.stat-row {
  display: flex;
  gap: 16px;
  margin: 16px 0;
  flex-wrap: wrap;
}
.stat-card {
  flex: 1;
  min-width: 140px;
  border-left: 4px solid #6366f1;
  padding: 12px 16px;
  background: #f8f8fc;
  page-break-inside: avoid;
}
.stat-card .stat-number {
  font-size: 24px;
  font-weight: 800;
  color: #6366f1;
  line-height: 1.1;
}
.stat-card .stat-label {
  font-size: 9px;
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
.highlight-box h3 { color: #6366f1; margin-top: 0; }
.highlight-box p, .highlight-box li { color: #e2e8f0; }

blockquote {
  border-left: 3px solid #6366f1;
  padding: 12px 20px;
  margin: 16px 0;
  font-style: italic;
  color: #475569;
  background: #fafaff;
  font-weight: 600;
}

.team-table td { padding: 10px 12px; }

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
  <div class="doc-title">UK Fintech CTO Pitch Deck</div>
  <div class="doc-subtitle">"Days NOT Months" — Legacy Core Banking Modernisation</div>
  <div class="doc-date">April 2026 · Confidential · Slides + Speaker Notes</div>
</div>

<div class="exec-summary">
  <h3>Deck Overview</h3>
  <p>This is the full pitch deck with speaker notes for a CTO presentation at a mid-size UK fintech. The deck runs 10 slides and is designed for a 20–30 minute presentation, either in-person or via screen share. The core message: Roll the Code's Orchestration System can reduce an 18-month legacy banking modernisation to weeks — deterministically, with fixed price, starting from one non-critical module. Speaker notes below each slide provide context, anticipated objections, and recommended emphasis points.</p>
</div>

<div class="slide-section">
<span class="slide-number">Slide 1</span>
<span class="slide-label">Title</span>

## Modernise Your Core Banking System. In Weeks, Not Years.

**Roll the Code — AI Agent Factory**

> *"Days NOT Months"*

Presented by Antal Károlyi, PhD · Co-founder & Board Member · April 2026

<div class="speaker-notes">
<strong>Speaker notes:</strong> Open with the tension. This CTO has lived through a failed or stalled legacy modernisation. Don't start with the solution — start with the recognition. Say: "You've probably sat in a meeting where someone said this refactor will take 18 months. We've built something specifically for that problem." The tagline is not a slogan — it's the summary of everything you're about to show them.
</div>
</div>

<div class="slide-section">
<span class="slide-number">Slide 2</span>
<span class="slide-label">The Problem</span>

## 18 months to update a core banking module. That's not an architecture problem. That's a delivery crisis.

<div class="stat-row">
  <div class="stat-card">
    <div class="stat-number">18mo</div>
    <div class="stat-label">Avg. module update cycle</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">60–70%</div>
    <div class="stat-label">Engineering capacity lost to maintenance</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">Compounding</div>
    <div class="stat-label">Technical debt per sprint</div>
  </div>
</div>

- UK mid-size fintechs spend the majority of engineering capacity **maintaining legacy systems**, not building the product their customers need
- Regulators demand faster change; **every sprint against the monolith** compounds risk and costs more than the last
- The longer you wait, the further competitors who are acting now will pull ahead

<div class="speaker-notes">
<strong>Speaker notes:</strong> Let the 18-month stat land. Don't rush past it. Ask them directly: "What's currently blocked because of your core system?" This opens the room. The CTO will tell you. That's the module you'll be pitching Phase 1 against. Note: if your specific prospect has a different number — use theirs. This is their pain, not a generic statistic.
</div>
</div>

<div class="slide-section">
<span class="slide-number">Slide 3</span>
<span class="slide-label">The Solution</span>

## We reverse-engineer your legacy system, generate a modern spec, and deliver a production-ready replacement — in weeks.

**Our Orchestration System:**

- **Read your codebase at scale** — static analysis, dependency mapping, behaviour extraction
- **Generate a validated modern specification** — human-readable, architect-reviewed, immediately actionable
- **Implement with deterministic AI orchestration** — multi-layered, architect-supervised, production-grade
- **Deploy to your stack** — tech-stack agnostic, deployment agnostic. Your infrastructure, your rules

<blockquote>Not vibe coding. Architect-supervised. Deterministic results.</blockquote>

<div class="speaker-notes">
<strong>Speaker notes:</strong> Stress "deterministic" — this single word separates us from every other AI shop the CTO has already dismissed. They've heard "AI-powered development" before and they're sceptical. The key differentiator is that this was built by software architects as a system, not assembled from AI tools by enthusiasts. If they ask how it works technically, that's the signal to go deeper — but don't lead with tech.
</div>
</div>

<div class="page-break"></div>

<div class="slide-section">
<span class="slide-number">Slide 4</span>
<span class="slide-label">How It Works</span>

## Three phases. Fixed scope at every gate.

| Phase | What Happens | Timeframe |
|---|---|---|
| **Phase 1: Reverse Engineering** | AI pipeline analyses the legacy codebase — static analysis, dependency mapping, behaviour extraction. Output: a clean, modern technical specification. You review and approve. | Days |
| **Phase 2: Implementation** | Agentic AI orchestration builds the replacement against the validated spec. Senior architects supervise every output. Milestone approval before proceeding to deployment. | Weeks |
| **Phase 3: Deploy & Hand Over** | Production-ready code, fully documented and tested. Deployed to your infrastructure. Full handover to your team — no lock-in, no retainer required. | Your timeline |

<div class="speaker-notes">
<strong>Speaker notes:</strong> Emphasise that Phase 1 alone has unblocked stalled projects. We have had clients who purchased Phase 1 — the reverse-engineering and spec — and then executed Phase 2 internally with their own team. The spec alone has commercial value. This reduces the perceived risk of the engagement considerably. Also note: "milestone approval before proceeding" is a control mechanism for the CTO, not a courtesy — it's contractual.
</div>
</div>

<div class="slide-section">
<span class="slide-number">Slide 5</span>
<span class="slide-label">Results</span>

## What this looks like in practice.

| Scenario | Legacy Situation | RTC Outcome |
|---|---|---|
| Reporting module | Planned as a 6-month internal refactor | Delivered in under 4 weeks |
| Enterprise integration | Stalled for 12+ months, no internal owner | Unblocked by reverse-engineering spec in days |
| Discovery-to-spec phase | Months of architectural archaeology | Reduced to days across multiple engagements |

*Client names withheld. Available under NDA on request.*

<div class="speaker-notes">
<strong>Speaker notes:</strong> These are real outcomes — we don't inflate numbers. If the CTO pushes back ("give me a client name"), acknowledge the NDA constraint and offer to arrange a reference call. The key point is specificity: "under 4 weeks" is verifiable, not "significantly faster." If you have a closer analogue to their specific module by the time of the meeting, use that instead. The more specific to their problem, the more credible the result.
</div>
</div>

<div class="slide-section">
<span class="slide-number">Slide 6</span>
<span class="slide-label">Use Cases</span>

## Start non-critical. Expand with confidence.

| Module | Legacy Pain | RTC Outcome |
|---|---|---|
| **Reporting & Analytics Layer** | Manual extraction, stale data, core DB coupling, no API layer | Modern API-connected reporting layer — delivered in weeks |
| **Onboarding & KYC Workflow** | 3rd-party dependencies, untestable integrations, compliance drift | Clean reimplementation — full spec + build, testable and auditable |
| **Payment Reconciliation** | Monolithic logic, manual overrides, untraceable edge cases | Modular, testable replacement — built from a reverse-engineered spec |

<div class="speaker-notes">
<strong>Speaker notes:</strong> The non-critical entry point is the most important element of the sales motion. It de-risks the decision for the CTO and gives them internal proof to show their board or risk function before committing to higher-value systems. Ask: "Which of these three modules maps closest to what you have stalled right now?" Then move toward the scoping conversation.
</div>
</div>

<div class="page-break"></div>

<div class="slide-section">
<span class="slide-number">Slide 7</span>
<span class="slide-label">Why Now</span>

## The window is 6–9 months.

- AI-assisted software delivery has moved from **experiment to production** across UK enterprise in 2025–2026
- UK fintech firms acting in 2026 will carry the **architectural advantage** for the next decade
- Regulatory pressure — FCA, Basel, DORA — is **increasing the cost of stale systems** with each passing quarter
- Early movers are already reducing legacy maintenance costs and **accelerating feature velocity**
- Waiting means handing the initiative to **competitors who are moving now**

<blockquote>The question is not whether to modernise. It's whether you lead or follow.</blockquote>

<div class="speaker-notes">
<strong>Speaker notes:</strong> Urgency here is real, not manufactured. We're 12–18 months into the AI delivery curve. The early window is genuinely closing. Frame this as a strategic decision, not a vendor selection. The CTO who acts in Q2 2026 has a meaningfully different outcome than the one who waits for internal sign-off until Q4. Don't be alarmist — be factual. The regulatory pressure from DORA in particular is a concrete forcing function worth mentioning by name.
</div>
</div>

<div class="slide-section">
<span class="slide-number">Slide 8</span>
<span class="slide-label">Why Roll the Code</span>

## Architects who built a system. Not prompt engineers with a deck.

<table class="team-table">
  <thead>
    <tr>
      <th>Name</th>
      <th>Role</th>
      <th>Relevant Depth</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Gábor Tatár</strong></td>
      <td>AI Orchestration Lead</td>
      <td>Product owner of the Orchestration System. Software architect. 20+ years enterprise delivery.</td>
    </tr>
    <tr>
      <td><strong>Ákos Karacs</strong></td>
      <td>QA & Architecture</td>
      <td>Built the determinism and quality layer of our pipeline. Business analyst and software architect.</td>
    </tr>
    <tr>
      <td><strong>Roland Repka</strong></td>
      <td>Senior Full-Stack</td>
      <td>Production delivery. Translates orchestration output into deployable, maintainable, documented code.</td>
    </tr>
    <tr>
      <td><strong>Steve Balogh</strong></td>
      <td>Enterprise IT Adviser</td>
      <td>Enterprise IT advisory — ensures every engagement is commercially sound and enterprise-viable.</td>
    </tr>
  </tbody>
</table>

**SignCoders** — our cooperation partner — is a social enterprise employing Deaf and hard-of-hearing professionals in mixed Deaf–hearing tech teams. They provide agentic AI implementation and UX/UI. Genuine technical depth. A diversity story that matters to enterprise procurement. Not a subcontractor — a partner.

<div class="speaker-notes">
<strong>Speaker notes:</strong> The CTO needs to know there are real engineers behind this — mention Gábor and Ákos by name and by specific credential. The question they'll be forming internally: "Are these people who could sit in a technical review with my architects?" The answer is yes. SignCoders is a genuine differentiator for enterprise procurement, especially in UK financial services where supplier diversity is increasingly scrutinised.
</div>
</div>

<div class="page-break"></div>

<div class="slide-section">
<span class="slide-number">Slide 9</span>
<span class="slide-label">The Offer</span>

## A low-risk starting point. A high-impact outcome.

**Proposed Engagement:**

- **Scoping call (45 min)** — map target module, define fixed scope, agree timeline
- **Fixed-scope proposal** — delivered within 5 working days
- **Pilot delivery** — one non-critical module, fixed price, milestone-based
- **Expand on success** — further modules under a separate fixed-scope agreement

**Pricing:**

<div class="stat-row">
  <div class="stat-card">
    <div class="stat-number">€50K–€200K</div>
    <div class="stat-label">Mid-size non-critical solutions</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">Weeks</div>
    <div class="stat-label">Delivery timeframe</div>
  </div>
  <div class="stat-card">
    <div class="stat-number">Fixed</div>
    <div class="stat-label">Scope and price — no T&M</div>
  </div>
</div>

*Fixed scope. Fixed price. No open-ended retainer. If the pilot delivers — and we expect it to — expansion is a conversation, not a commitment.*

<div class="speaker-notes">
<strong>Speaker notes:</strong> Don't leave the meeting without booking the scoping call. The pilot structure removes the "what if it fails" objection — fixed price means their downside is capped. Fixed scope means there's no scope creep risk. The "expand on success" language is deliberate — it puts the CTO in control of the next decision, which reduces procurement anxiety. If they ask about the €50K–€200K range, the answer is: "The scoping call gives us the information to fix the number precisely within that range."
</div>
</div>

<div class="slide-section">
<span class="slide-number">Slide 10</span>
<span class="slide-label">Contact</span>

## Start with 45 minutes. Not 18 months.

**Antal Károlyi, PhD**
Co-founder & Board Member · Roll the Code

- antal@rollthecode.io
- rollthecode.io
- LinkedIn: /in/antalkarolyi

> *"Days NOT Months"*

One scoping call. A fixed-scope proposal within 5 working days. A pilot on one non-critical module that proves the approach before you commit to anything larger.

<div class="speaker-notes">
<strong>Speaker notes:</strong> Close with the tagline. It's not a slogan — it's the one-sentence summary of everything you've just shown them. The ask is minimal: one 45-minute call. If they say "we need to think about it," offer to send the one-pager and follow up in 5 working days. If they ask for a case study, offer an NDA-protected reference. If they ask about procurement process, offer to route through their preferred channels — we can adapt the contract structure.
</div>
</div>

<div class="highlight-box">
  <h3>Deck Summary — Key Messages for the CTO</h3>
  <ul>
    <li>Your 18-month update cycle is a delivery problem, not an architecture problem — and it is solvable now</li>
    <li>Our Orchestration System reverse-engineers, specifies, and rebuilds legacy modules in weeks — deterministically, with fixed price</li>
    <li>This was built by software architects with decades of enterprise experience — not prompt engineers</li>
    <li>Start with one non-critical module. Prove the approach. Expand with confidence.</li>
    <li>The window is 6–9 months. The firms that act in 2026 carry the architectural advantage for a decade.</li>
    <li>One 45-minute scoping call. Fixed-scope proposal within 5 working days. No risk to start.</li>
  </ul>
</div>
