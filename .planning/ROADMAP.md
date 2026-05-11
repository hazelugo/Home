# Roadmap: hazelugo.com Portfolio Rebuild

## Overview

Evolve a live single-file portfolio from a cybersecurity/network resume page into a dual-track portfolio that leads with AI development while retaining security/network credentials. Three phases: content updates to the existing sections, new sections and projects, then a resume page and final quality gate.

## Phases

**Phase Numbering:**
- Integer phases (1, 2, 3): Planned milestone work
- Decimal phases (2.1, 2.2): Urgent insertions (marked with INSERTED)

Decimal phases appear between their surrounding integers in numeric order.

- [ ] **Phase 1: Content Updates** - Update hero, about, and skills to reflect the dual-track identity
- [ ] **Phase 2: New Sections & Projects** - Add Workflow section, three AI projects, and update navigation
- [ ] **Phase 3: Resume Page & Quality Gate** - Build resume.html and verify mobile, accessibility, and no-JS constraints

## Phase Details

### Phase 1: Content Updates
**Goal**: The existing sections accurately represent the dual-track (AI + security/network) identity
**Depends on**: Nothing (first phase)
**Requirements**: HERO-01, HERO-02, HERO-03, ABUT-01, SKIL-01, SKIL-02
**Success Criteria** (what must be TRUE):
  1. Hero subtitle reads "AI, Security & Network Professional" and degree line shows no "Graduating" qualifier or year
  2. OG meta description and title reflect AI + security/network dual-track identity
  3. About section contains a paragraph covering shipped AI apps, AI-assisted workflow, and production deployments
  4. Skills section has a visible "AI Development & Integration" category with the correct tool list, and existing four categories are unchanged
**Plans**: TBD
**UI hint**: yes

### Phase 2: New Sections & Projects
**Goal**: Visitors can read the AI workflow methodology and explore all three new AI projects above the existing security labs
**Depends on**: Phase 1
**Requirements**: WKFL-01, WKFL-02, WKFL-03, WKFL-04, PROJ-01, PROJ-02, PROJ-03, PROJ-04, PROJ-05, NAVM-01, NAVM-02
**Success Criteria** (what must be TRUE):
  1. A "How I Work" section appears between Skills and Projects with three named phases (GSD, Claude Code + MCPs, Impeccable), each with a short description
  2. Song Tool, Workout App, and Emma's Math Quest accordion entries exist above the five security labs, each with correct stack tags, links, and category badges
  3. All five existing security/network lab projects remain present and functional
  4. Sidebar nav lists About, Skills, Workflow, Projects, Experience, Contact in that order, with Workflow scroll-linked active state working
  5. Section numbers throughout the page are correct after the Workflow section insertion
**Plans**: TBD
**UI hint**: yes

### Phase 3: Resume Page & Quality Gate
**Goal**: A printable resume page exists and the full site passes mobile, accessibility, and no-JS constraints
**Depends on**: Phase 2
**Requirements**: RESU-01, RESU-02, RESU-03, RESU-04, RESU-05, RESU-06, QUAL-01, QUAL-02, QUAL-03
**Success Criteria** (what must be TRUE):
  1. resume.html exists with cybersecurity resume content, minimal print-friendly styling, a "Download PDF" link, and a link back to the main site
  2. Main site footer and contact section both link to resume.html
  3. All new and modified sections display correctly at 390px viewport width
  4. A follow-up Impeccable audit returns no Critical or High findings
  5. Core content is readable with JavaScript disabled and the nav degrades gracefully
**Plans**: TBD
**UI hint**: yes

## Progress

**Execution Order:**
Phases execute in numeric order: 1 → 2 → 3

| Phase | Plans Complete | Status | Completed |
|-------|----------------|--------|-----------|
| 1. Content Updates | 0/? | Not started | - |
| 2. New Sections & Projects | 0/? | Not started | - |
| 3. Resume Page & Quality Gate | 0/? | Not started | - |
