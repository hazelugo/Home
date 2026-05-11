# Phase 2: New Sections & Projects - Context

**Gathered:** 2026-05-11
**Status:** Ready for planning

<domain>
## Phase Boundary

Add the "How I Work" workflow section, three new AI projects to the existing accordion, update sidebar navigation order, and renumber all section display labels. This phase changes HTML structure and adds CSS tokens — no layout redesign. Scope: `index.html` only.

</domain>

<decisions>
## Implementation Decisions

### Workflow Section — Structure
- **D-01:** Use the existing `.skill-row` pattern verbatim — `.skill-category` (mono label, left column, fixed width) + `.skill-list` (content text, right). Zero new CSS classes needed; reuses the identical markup pattern from the Skills section.
- **D-02:** Section heading: "How I work." — matches the lowercase-with-period voice of "What I work with." and "Hands-on projects."
- **D-03:** Section ID: `id="workflow"`, section class: `class="section"` (no `section-alt` — alternate pattern goes About→Skills→Workflow→Projects→Experience→Contact, keeping alternation consistent)
- **D-04:** Section number display label: `03` (Workflow inserts between Skills=02 and Projects=04)

### Workflow Section — Three Phase Rows
- **D-05:** Left column labels (`.skill-category` mono column): "Spec & Planning", "Build", "Quality Gate" — short, fits the fixed-width mono column without wrapping
- **D-06:** Copy direction: executor writes 2-3 sentences per phase in the established site voice (first person, specific, no filler — same register as About paragraphs). Use the brief as reference material for content, not verbatim copy.
- **D-07:** Phase 1 content reference (GSD): meta-prompting + spec-driven dev system, structured discovery process, parallel research agents, atomic git commits, `.planning/` markdown as persistent memory
- **D-08:** Phase 2 content reference (Claude Code + MCPs): VS Code terminal, Claude Code as primary coding agent, Supabase MCP + Gemini MCP + Claude-native tools, context managed via PROJECT.md/REQUIREMENTS.md/STATE.md/ROADMAP.md
- **D-09:** Phase 3 content reference (Impeccable): 23-command design intelligence system, `/teach` profiles audience, `/audit` runs 5-dimension quality check with severity ratings, individual commands resolve findings

### Navigation Update
- **D-10:** Sidebar nav `<li>` order: About, Skills, Workflow, Projects, Experience, Contact
- **D-11:** Workflow nav item: `<a href="#workflow" class="sidebar-item" data-section="workflow">Workflow</a>`
- **D-12:** Section renumbering — display labels only (`.section-num` spans):
  - About: `01` (unchanged)
  - Skills: `02` (unchanged)
  - Workflow: `03` (new)
  - Projects: `04` (was `03`)
  - Experience: `05` (was `04`)
  - Contact: `06` (was `05`)

### New AI Projects — Accordion Entries
- **D-13:** Three new projects inserted ABOVE the existing five security/network labs. Order: Song Tool, Workout App, Emma's Math Quest, then the existing five.
- **D-14:** Project numbers resequenced: Song Tool=01, Workout App=02, Emma's Math Quest=03, Vulnerability Assessment Lab=04, SIEM Lab=05, Network Traffic Analysis=06, Segmented Home Network=07, A/V Production LAN=08
- **D-15:** All three use the identical `<button type="button" class="project-item" aria-expanded="false" onclick="toggleProject(this)">` accordion pattern

### New AI Projects — Link Row
- **D-16:** A `.project-links` row appears between `.project-detail-text` and `.project-tools` inside the expanded `.project-detail`
- **D-17:** Link text: "View live →" for the live URL, "GitHub →" for the repo — plain text links styled as small, understated anchors (font-size: 0.75rem, color: var(--accent), text-decoration: none, hover underline)
- **D-18:** All three projects have both a live URL and a GitHub repo:
  - Song Tool: live https://haze-song-tool.vercel.app — repo https://github.com/hazelugo/Song-Tool
  - Workout App: live https://workout.hazelugo.com — repo https://github.com/hazelugo/Workout-App
  - Emma's Math Quest: live https://emath.hazelugo.com — repo https://github.com/hazelugo/EmmaApp
- **D-19:** Links open in `target="_blank" rel="noopener noreferrer"`

### New AI Projects — Category Tags
- **D-20:** Full-Stack tag: `class="project-tag tag-fullstack"` — teal color palette
  - CSS tokens: `--tag-fullstack-bg: oklch(91% 0.07 185)` / `--tag-fullstack-text: oklch(42% 0.15 185)`
- **D-21:** Frontend tag: `class="project-tag tag-frontend"` — rose/pink color palette
  - CSS tokens: `--tag-frontend-bg: oklch(93% 0.06 0)` / `--tag-frontend-text: oklch(48% 0.18 0)`
- **D-22:** Tag tokens added to `:root` CSS block alongside existing `--tag-*` tokens

### New AI Projects — Content Summary
- **D-23:** Song Tool: "Full-Stack" tag, stack chips: Next.js 15, TypeScript, Supabase, Drizzle ORM, Vercel — description covers music catalog/playlist builder, technical decisions (JWT sessions, tsvector search, fractional position indexing, defense-in-depth auth, Playwright E2E)
- **D-24:** Workout App: "Full-Stack" tag, stack chips: JavaScript, Supabase, Vercel, Google OAuth — description covers evolution from local viewer to multi-user app, per-user RLS, OAuth, Vercel SPA routing for redirects
- **D-25:** Emma's Math Quest: "Frontend" tag, stack chips: Vue 3, Vite, Tailwind CSS v4, Web Audio API — description covers adaptive difficulty (rolling 10-answer window, 80% target), synthesized audio (no external files), CSS confetti, 60px touch targets, built for a real 6-year-old user

### Claude's Discretion
- Exact prose for the three Workflow phase descriptions (content reference in D-07/D-08/D-09, Claude writes the copy)
- Exact prose for the three project descriptions (content summary in D-23/D-24/D-25, Claude writes the copy)
- `.reveal` delay classes for the three new `.skill-row`-style workflow rows (follow the existing pattern from Skills section)
- Reveal delay classes for the new project items (continue the existing stagger pattern)

</decisions>

<canonical_refs>
## Canonical References

**Downstream agents MUST read these before planning or implementing.**

### Project Planning
- `.planning/PROJECT.md` — Core value, constraints, voice notes
- `.planning/REQUIREMENTS.md` — WKFL-01..04, PROJ-01..05, NAVM-01..02
- `.planning/phases/01-content-updates/01-CONTEXT.md` — Phase 1 decisions (single-file constraint, voice, existing patterns)

### Source File
- `index.html` — The only file being edited. Read it to understand the current skill-row pattern, project-item accordion pattern, existing tag tokens, and nav structure before making any changes.

### No external specs — all decisions captured above

</canonical_refs>

<code_context>
## Existing Code Insights

### Reusable Assets
- `.skill-row` + `.skill-category` + `.skill-list`: exact markup to reuse for all three Workflow phase rows
- `.project-item` accordion button with `.project-row` / `.project-expand` / `.project-detail` / `.project-tools`: exact markup to replicate for three new projects
- `.section-num` + `.section-heading` + `.section-header` pattern for the Workflow section header
- `.certs-strip` section pattern (no `section-alt` class) — reference for a non-alternating section if needed

### Established Patterns
- Tag tokens: `:root` block has `--tag-network-bg`, `--tag-network-text` etc. — add `--tag-fullstack-*` and `--tag-frontend-*` in the same block
- All project tag classes follow `.tag-{name}` convention using the CSS tokens
- Project items use `onclick="toggleProject(this)"` — not event listeners — keep consistent
- Reveal delays: `.reveal`, `.reveal-d1`, `.reveal-d2`, `.reveal-d3`, `.reveal-d4` are defined in CSS

### Integration Points
- Sidebar `<ul>` in `<nav class="sidebar-nav">`: new `<li>` for Workflow inserts between Skills and Projects
- IntersectionObserver in `<script>`: already targets `section[id]` — new `<section id="workflow">` is automatically observed
- Section numbers: `.section-num` spans are display-only text, not tied to any JS logic — safe to change
- `.skills-table` immediately precedes `#projects` in the current DOM — `#workflow` section inserts between them

</code_context>

<specifics>
## Specific Ideas

- The "How I Work" section should feel like a natural extension of Skills — same flat typographic treatment, same visual weight. Not a hero section, not a callout box.
- Project links ("View live →", "GitHub →") should be subtle — smaller than the description text, accent color, understated. They shouldn't compete with the project name/description.
- The note "Built for a real user with real constraints — not a demo" in Emma's Math Quest description is a strong closer — keep it or a close variant.

</specifics>

<deferred>
## Deferred Ideas

None — discussion stayed within phase scope.

</deferred>

---

*Phase: 02-new-sections-projects*
*Context gathered: 2026-05-11*
