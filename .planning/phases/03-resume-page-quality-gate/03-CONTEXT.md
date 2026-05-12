# Phase 3: Resume Page & Quality Gate - Context

**Gathered:** 2026-05-11
**Status:** Ready for planning

<domain>
## Phase Boundary

Create `resume.html` at the project root, link it from the main site footer and contact section, fix two carry-over review items in `index.html` (hero CTA text, og:url). Verify mobile layout at 390px for new sections. Two files touched: `index.html` (links + fixes) and `resume.html` (new file).

</domain>

<decisions>
## Implementation Decisions

### resume.html — Content Track
- **D-01:** Cybersecurity/network resume only — not dual-track. resume.html is the professional IT resume; AI work lives at index.html.
- **D-02:** Four sections: Work History, Education, Certifications, Skills
- **D-03:** Brief mention of AI development track — one short line or small subsection indicating breadth (e.g., "Also building full-stack AI applications" or similar). Does not dominate the document.

### resume.html — Content Source
- **D-04:** Work history sourced from index.html existing content:
  - Mission Consolidated Independent School District — Attendance & Purchasing / IT Liaison (Sep 2019 – Present)
  - Charter Communications — Bilingual Billing & Tech Support (Mar 2018 – Sep 2019)
- **D-05:** Education: B.A.T. — Computer Information Technology, South Texas College (completed — no date badge)
- **D-06:** Certifications: Security+, Network+, A+, ISC2 CC — All Active
- **D-07:** Skills: sourced from index.html skills table — Networking, Security, Systems & OS, Hardware & Tools categories (not the AI Development & Integration row, which belongs in portfolio context)

### resume.html — Styling
- **D-08:** Minimal browser default + print CSS. No external fonts loaded — system font stack only. Fast, print-ready.
- **D-09:** `@media print` block hides the back link and download button (nav/action elements not needed on paper)
- **D-10:** White background, black text. max-width ~720px, centered, comfortable margins.
- **D-11:** `<a href="/" class="back-link">← Back to portfolio</a>` visible header link
- **D-12:** `<a href="resume.pdf">Download PDF</a>` button or link visible above the fold

### Links from index.html

**Footer:**
- **D-13:** Add a 4th footer item: `<a href="resume.html">View Resume</a>` alongside the existing email link
- **D-14:** Footer currently ends with `<a href="mailto:haze.lugo@gmail.com">haze.lugo@gmail.com</a>` — new link added as a sibling `<span>` or `<a>` in the same flex row

**Contact section:**
- **D-15:** Add a new `.contact-link` row for resume.html — matching the Email/LinkedIn/GitHub/Phone pattern (icon + label + value)
- **D-16:** Icon: a document/file SVG (can use a simple page icon)
- **D-17:** Label text: "Resume", value text: "hazelugo.com/resume" (the HTML version, not the PDF)
- **D-18:** `href="resume.html"` — opens the resume page, not the PDF directly

### Carry-over Fixes (index.html)
- **D-19:** Hero CTA text: "View Lab Work" → "View Projects" (the link itself stays `href="#projects"`, only the text changes)
- **D-20:** Add `<meta property="og:url" content="https://hazelugo.com/" />` to the `<head>` block, after the existing `og:type` tag

### Quality Gate (QUAL-01..03)
- **D-21:** Mobile 390px check is a verification/browser check, not a code task — the executor should visually confirm new sections (#workflow, new project entries) display correctly at 390px. If any issues found, fix them.
- **D-22:** Impeccable audit (QUAL-02) is part of the verification step — the verifier checks for new Critical/High issues introduced by Phases 1-3. No new CSS patterns introduced that obviously violate the audit criteria.
- **D-23:** No-JS compatibility (QUAL-03): core content must be readable with JS disabled. The workflow section and project entries are static HTML — they render without JS. The sidebar and project accordion degrading gracefully with JS disabled was already true in the base site.

### Claude's Discretion
- Exact prose for the one-line AI development mention in resume.html (D-03)
- resume.html document structure / heading hierarchy
- Document icon SVG for the contact-link row (D-16)

</decisions>

<canonical_refs>
## Canonical References

**Downstream agents MUST read these before planning or implementing.**

### Project Planning
- `.planning/PROJECT.md` — Core value, constraints, voice notes
- `.planning/REQUIREMENTS.md` — RESU-01..06, QUAL-01..03

### Source Files
- `index.html` — Read before modifying (links, CTA fix, og:url)
- `resume.pdf` — Exists at root, is the download target for D-12

### Prior Phase Decisions
- `.planning/phases/01-content-updates/01-CONTEXT.md` — Single-file constraint, voice
- `.planning/phases/02-new-sections-projects/02-CONTEXT.md` — Design patterns established

### No external specs — all decisions captured above

</canonical_refs>

<code_context>
## Existing Code Insights

### Reusable Assets
- `.contact-link` pattern (Email/LinkedIn/GitHub/Phone rows): exact HTML structure to replicate for the resume row (D-15/D-16/D-17/D-18)
- `.btn-ghost` class: could use for the resume.html "View Resume" footer link if styled as a button, but plain `<a>` is fine
- Footer flex row: `<footer>` has `display: flex; justify-content: space-between; flex-wrap: wrap; gap: 1rem`

### Integration Points
- Footer `<a href="mailto:...">` is the last child — new resume link appended after it
- Contact section `.contact-links` div contains the 4 existing contact rows — new row appended as 5th child
- `<head>` block: `og:url` goes after `<meta property="og:type" content="website" />` (line ~19)
- Hero actions `.hero-actions` div: "View Lab Work" text is in `<a href="#projects" class="btn-primary">` — change text only

### New File
- `resume.html` is a new standalone file at the project root
- It should have its own `<head>` with title "Hector Lugo — Resume" and minimal CSS in a `<style>` block
- No sidebar, no JS, no external dependencies

</code_context>

<specifics>
## Specific Ideas

- resume.html should feel like a clean, professional document — not a portfolio page. Plain, structured, scannable in under 30 seconds.
- The back link and download button are the only interactive elements.
- The AI development mention (D-03) could be a single italic line at the end of the skills section or a brief "Also" line after the main content — low-key, not a selling point, just an honest breadth indicator.

</specifics>

<deferred>
## Deferred Ideas

None — discussion stayed within phase scope.

</deferred>

---

*Phase: 03-resume-page-quality-gate*
*Context gathered: 2026-05-11*
