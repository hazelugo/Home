# Requirements: hazelugo.com Portfolio Rebuild

**Defined:** 2026-05-10
**Core Value:** A recruiter or hiring manager in any of three tracks — AI development, cybersecurity, or network — should finish reading in under 5 minutes and think "this person knows exactly what they're doing."

## v1 Requirements

### Hero

- [ ] **HERO-01**: Page subtitle reads "AI, Security & Network Professional" in the hero section
- [ ] **HERO-02**: Degree line displays as "B.A.T. — Computer Information Technology" with no "Graduating" qualifier or year
- [ ] **HERO-03**: OG meta title and description reflect the dual-track identity (AI + security/network)

### About

- [ ] **ABUT-01**: About section includes a paragraph covering the AI development track — shipped apps, AI-assisted workflow, production deployments

### Skills

- [ ] **SKIL-01**: Skills section includes a new "AI Development & Integration" category with: Claude API / Anthropic SDK, Gemini CLI, MCP orchestration, GSD, Impeccable, Next.js 16, TypeScript, Drizzle ORM, Vue 3, Vite, Supabase, Vercel, GitHub, context engineering
- [ ] **SKIL-02**: Existing four skill categories (Networking, Security, Systems & OS, Hardware & Tools) remain unchanged

### Workflow Section

- [ ] **WKFL-01**: A "How I Work" section exists in the page between Skills and Projects
- [ ] **WKFL-02**: Section has three named phases: Phase 1 (GSD — spec & planning), Phase 2 (Claude Code + MCPs — build), Phase 3 (Impeccable — quality gate)
- [ ] **WKFL-03**: Each phase has a short label and 2-3 sentence description in the existing flat, typographic style (no icons)
- [ ] **WKFL-04**: "Workflow" appears as a nav item in the sidebar between Skills and Projects, with correct scroll-linked active state

### Projects

- [ ] **PROJ-01**: Song Tool accordion entry exists with description, stack tags (Next.js 16, TypeScript, Supabase, Drizzle ORM, Vercel), live URL (https://haze-song-tool.vercel.app), GitHub link (https://github.com/hazelugo/Song-Tool), and "Full-Stack" category badge
- [ ] **PROJ-02**: Workout App accordion entry exists with description, stack tags (JavaScript, Supabase, Vercel, Google OAuth), live URL (https://workout.hazelugo.com), GitHub link (https://github.com/hazelugo/Workout-App), and "Full-Stack" category badge
- [ ] **PROJ-03**: Emma's Math Quest accordion entry exists with description, stack tags (Vue 3, Vite, Tailwind CSS v4, Web Audio API), GitHub link (https://github.com/hazelugo/EmmaApp), and "Frontend" category badge
- [ ] **PROJ-04**: Three new AI projects appear above the five existing security/network labs in the accordion
- [ ] **PROJ-05**: All five existing security/network lab projects remain present and functional (Vulnerability Assessment Lab, SIEM Log Analysis Lab, Network Traffic Analysis, Segmented Home Network Lab, A/V Production LAN)

### Navigation & Section Numbering

- [ ] **NAVM-01**: Section numbers updated throughout (Workflow section added, all subsequent sections renumbered)
- [ ] **NAVM-02**: Sidebar nav order is: About, Skills, Workflow, Projects, Experience, Contact

### Resume Page

- [ ] **RESU-01**: `resume.html` exists at project root with cybersecurity resume content (work history, education, certifications, skills)
- [ ] **RESU-02**: `resume.html` uses minimal styling — white background, black text, no sidebar, print-friendly
- [ ] **RESU-03**: `resume.html` has a "Download PDF" link pointing to `resume.pdf`
- [ ] **RESU-04**: `resume.html` has a visible link back to the main site
- [ ] **RESU-05**: Main site footer includes a link to `resume.html`
- [ ] **RESU-06**: Contact section links to `resume.html` (alongside Download Resume button)

### Quality & Compatibility

- [ ] **QUAL-01**: All new and modified sections pass mobile layout check at 390px viewport
- [ ] **QUAL-02**: No Critical or High findings in a follow-up Impeccable audit
- [ ] **QUAL-03**: Core content readable with JavaScript disabled (nav degrades gracefully)

## v2 Requirements

### Content

- **CONT-01**: Blog or writing section for technical posts and case studies
- **CONT-02**: Additional AI projects as they ship
- **CONT-03**: Case study detail pages for major projects (Song Tool deep-dive)

### Features

- **FEAT-01**: Contact form (currently email-only)
- **FEAT-02**: Project filter by category tag on the projects accordion

## Out of Scope

| Feature | Reason |
|---|---|
| npm / build tools / frameworks | Single-file constraint — no build step |
| Dark mode | Light theme is the deliberate differentiator |
| Design system redesign | Existing OKLCH + typography is strong — extend only |
| Backend / server-side logic | Static site only |
| Rewriting existing security/network project content | Content is accurate and well-written |
| Rewriting existing work history content | Content is accurate — update dates/status only |
| More than one new HTML page | `resume.html` only; routing not available |
| OAuth or authentication | No user accounts needed for a portfolio |

## Traceability

| Requirement | Phase | Status |
|---|---|---|
| HERO-01 | Phase 1 | Pending |
| HERO-02 | Phase 1 | Pending |
| HERO-03 | Phase 1 | Pending |
| ABUT-01 | Phase 1 | Pending |
| SKIL-01 | Phase 1 | Pending |
| SKIL-02 | Phase 1 | Pending |
| WKFL-01 | Phase 2 | Pending |
| WKFL-02 | Phase 2 | Pending |
| WKFL-03 | Phase 2 | Pending |
| WKFL-04 | Phase 2 | Pending |
| PROJ-01 | Phase 2 | Pending |
| PROJ-02 | Phase 2 | Pending |
| PROJ-03 | Phase 2 | Pending |
| PROJ-04 | Phase 2 | Pending |
| PROJ-05 | Phase 2 | Pending |
| NAVM-01 | Phase 2 | Pending |
| NAVM-02 | Phase 2 | Pending |
| RESU-01 | Phase 3 | Pending |
| RESU-02 | Phase 3 | Pending |
| RESU-03 | Phase 3 | Pending |
| RESU-04 | Phase 3 | Pending |
| RESU-05 | Phase 3 | Pending |
| RESU-06 | Phase 3 | Pending |
| QUAL-01 | Phase 3 | Pending |
| QUAL-02 | Phase 3 | Pending |
| QUAL-03 | Phase 3 | Pending |

**Coverage:**
- v1 requirements: 26 total
- Mapped to phases: 26
- Unmapped: 0 ✓

---
*Requirements defined: 2026-05-10*
*Last updated: 2026-05-10 after roadmap creation*
