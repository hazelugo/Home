# Phase 1: Content Updates - Context

**Gathered:** 2026-05-10
**Status:** Ready for planning

<domain>
## Phase Boundary

Update existing sections (hero, about, skills) so the portfolio accurately represents a dual-track AI + security/network identity. This phase changes content and copy only — no new sections, no layout changes, no new pages. Scope: `index.html` edits only.

</domain>

<decisions>
## Implementation Decisions

### Hero Role Subtitle
- **D-01:** Change from "Cybersecurity &amp; Network Professional" to "AI, Security &amp; Network Professional" — exact string, ampersand encoded

### Hero Description Paragraph
- **D-02:** Update degree reference: "graduating B.S." → "B.A.T." with no graduating qualifier or year
- **D-03:** Add an AI sentence using the "shipped apps + workflow" angle — concrete and factual, not aspirational. Model: "Three shipped full-stack apps, AI-assisted development workflow, and production deployments on Vercel." Keep it grounded, no tool-name-dropping in this paragraph (tools go in About).
- **D-04:** The rest of the paragraph ("Bilingual. Mission-focused. Building systems that defend and connect.") stays unchanged

### Hero Sub-Line
- **D-05:** Keep "CompTIA Trifecta Certified · ISC2 CC · South Texas" unchanged — the new subtitle already signals the AI track; this line stays factual/credential-focused

### About Section — AI Paragraph
- **D-06:** New AI paragraph inserted as the third paragraph — after the lab work paragraph, before the bilingual/availability paragraph
- **D-07:** Length: 3-4 sentences, same density and tone as the existing paragraphs. Grounded and specific; no tool name-dropping beyond what's necessary.
- **D-08:** Content must cover: shipped full-stack apps, AI-assisted development workflow, production deployments. Reference the work as a natural extension of the security/network background, not a pivot.
- **D-09:** Do not name specific app titles (Song Tool, Workout App, Emma's Math Quest) in the About paragraph — those are in the Projects section

### About Section — Paragraph 3 Update
- **D-10:** The existing third paragraph ("fluent in English and Spanish, graduating May 2026, looking to make the full transition") must be updated:
  - Remove "graduating May 2026" → degree is complete
  - Remove "make the full transition" framing → transition is done, already in the role
  - Keep the bilingual mention and South Texas/open to remote context
  - Present tense: available now, not transitioning

### Skills Table — New Category
- **D-11:** "AI Development &amp; Integration" is the first row in the skills table — AI leads
- **D-12:** Tool list (exact): Claude API / Anthropic SDK, Gemini CLI, MCP orchestration (Supabase MCP, Gemini MCP, Claude-native tools), GSD, Impeccable, Next.js 16 App Router, TypeScript, Drizzle ORM, Vue 3, Vite, Supabase (PostgreSQL, auth, row-level security), Vercel, GitHub / version control, Context engineering via structured markdown
- **D-13:** Existing four categories (Networking, Security, Systems &amp; OS, Hardware &amp; Tools) remain unchanged in content and order — they follow the new AI row

### OG Meta
- **D-14:** Update `og:title` and `og:description` to reflect dual-track identity. The description currently references "Graduating May 2026" which is outdated. New description should surface AI development alongside the existing security/network credentials.
- **D-15:** `<title>` element also updated to remove "Cybersecurity &amp; Network Professional" alone — match the new dual-track framing

### Claude's Discretion
- Exact wording for the AI paragraph in About — user established the content requirements (shipped apps, AI workflow, production deployments), Claude writes copy matching the existing voice
- Exact wording for paragraph 3 update — user set the direction (graduated, available, remove transition framing), Claude writes the copy
- Exact OG meta copy — Claude writes within the established dual-track framing

</decisions>

<canonical_refs>
## Canonical References

**Downstream agents MUST read these before planning or implementing.**

### Project Planning
- `.planning/PROJECT.md` — Core value, constraints, voice notes (no "passionate", no "leverage", first person)
- `.planning/REQUIREMENTS.md` — HERO-01..03, ABUT-01, SKIL-01..02 are the v1 requirements for this phase

### Source File
- `index.html` — The file being edited. All changes go here. Single-file architecture.

### No external specs — requirements fully captured in decisions above

</canonical_refs>

<code_context>
## Existing Code Insights

### Reusable Assets
- `.hero-role` div: current text "Cybersecurity &amp; Network Professional" → replace with "AI, Security &amp; Network Professional"
- `.hero-sub` div: current text "CompTIA Trifecta Certified · ISC2 CC · South Texas" → no change
- `.hero-desc` paragraph: current text contains "graduating B.S." and no AI mention → update per D-02, D-03, D-04
- `.about-text p` paragraphs: currently 3 — insert new AI paragraph as 3rd (0-indexed: before the last one)
- `.skill-row` divs: currently 4 rows — prepend new AI row as first child of `.skills-table`
- `<title>` element and OG meta tags in `<head>` → update per D-14, D-15

### Established Patterns
- Skill rows use `font-family: var(--font-mono)` on the category label with `color: var(--accent-2)`
- Skill list text uses `color: var(--text-muted)` and `font-size: 0.95rem`
- All paragraph text in About uses `color: var(--text-muted)` with `<strong>` highlights in `color: var(--text)`
- Comma-separated tool lists in skill rows (no bullets, no line breaks)

### Integration Points
- Phase 2 will add section renumbering — the skills section is currently "02", which will shift when Workflow section is inserted. Phase 1 does NOT renumber — that's Phase 2's job.
- The About section `reveal` animation classes must be preserved on any new paragraph (add `class="reveal reveal-d3"` or appropriate delay)

</code_context>

<specifics>
## Specific Ideas

- The new skills category label should match existing mono/uppercase style: "AI Development & Integration" using `var(--accent-2)` color token
- The AI paragraph in About should use the same `<strong>` inline emphasis pattern for key terms (as other About paragraphs do)
- Voice from brief: "someone who builds and defends systems with rigor" — this through-line applies to the AI content too

</specifics>

<deferred>
## Deferred Ideas

None — discussion stayed within phase scope.

</deferred>

---

*Phase: 01-content-updates*
*Context gathered: 2026-05-10*
