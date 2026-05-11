# GSD Project Brief — hazelugo.com Portfolio Rebuild

> Feed this document into `/gsd-new-project` when prompted for project context.
> The site is a single `index.html` file. There is no framework, no build step, no dependencies.
> All changes are vanilla HTML, CSS, and JavaScript.

---

## What This Project Is

A portfolio site rebuild for Hector Lugo (hazelugo.com). The site currently exists and is
live — it is not being built from scratch. The existing file is 1,935 lines of vanilla
HTML/CSS/JS, single file, deployed on the current host.

The goal is to evolve the site from a cybersecurity/network resume page into a dual-track
portfolio that leads with AI integration and development, while retaining the
cybersecurity/network credentials as a secondary track.

The existing design system is strong and should be preserved — OKLCH color tokens, Bricolage
Grotesque + Geist typography, accordion project pattern, sidebar navigation. Do not redesign.
Extend and update.

---

## What Needs To Change

### 1. Fix existing audit issues first (before any new content)

The GSD audit identified the following issues that must be resolved before adding anything new.
Address in this order:

**Critical:**
- C-1: `contact-link:hover` causes layout reflow — replace padding/margin animation with
  `transform: translateX` 
- C-2: Mobile `project-row` grid has 4 children in 3-column grid — toggle wraps to wrong
  position on mobile

**High:**
- H-1: No skip navigation link — add `<a href="#hero" class="skip-link">Skip to content</a>`
  as first element in body
- H-2: Active sidebar items missing `aria-current="location"` — add in IntersectionObserver
  callback
- H-3: Six elements use `0.67rem` font size — raise all to `0.75rem` globally
- H-4: Certifications strip has no mobile scroll affordance — stack vertically on mobile or
  add right-fade gradient
- H-5: Phone number displayed via CSS pseudo-element only — add `aria-label="Phone:
  956-432-3287"` to the anchor

**Medium/Low (second pass):**
- M-1: 3 hardcoded OKLCH values — replace with CSS tokens
- M-2: Dead `handleProjectKey` function — remove
- M-3: `#certifications` div in sidebar observer causes dead zone — change selector to
  `section[id]` only
- M-4: Geist 300 font weight loaded but unused — remove from Google Fonts URL
- L-1: Mobile sidebar focus not trapped when open — move focus to first link on open
- L-2: No `:active` states for touch — add to all interactive elements

---

### 2. Update existing content

**Hero section:**
- Change "Graduating May 2026" to degree completed
- Add AI integration as a third track alongside cybersecurity and network
- Update subtitle from "Cybersecurity & Network Professional" to reflect the broader identity
- Update open graph meta description to match

**About section:**
- Add a paragraph covering the AI development track — three shipped full-stack apps, AI-
  assisted development workflow, production deployments
- Mention GSD (spec-driven development system) and Impeccable (production UI quality gating)
  as part of the workflow, not just as tools

**Skills section:**
- Add a new skill category: "AI Development & Integration"
  - Claude API / Anthropic SDK
  - Gemini CLI / Antigravity
  - MCP orchestration (Supabase MCP, Gemini MCP, Claude-native tools)
  - GSD (meta-prompting, context engineering, spec-driven development)
  - Impeccable (production UI quality gating — audit, harden, adapt, polish, typeset)
  - Next.js 16 App Router, TypeScript, Drizzle ORM
  - Vue 3, Vite
  - Supabase (PostgreSQL, auth, row-level security)
  - Vercel deployment
  - GitHub / version control
  - Context engineering via structured markdown

---

### 3. Add new projects (extend the existing accordion pattern)

Add these three projects to the projects section using the identical accordion structure
already in place. Insert them before the existing security/network labs so AI projects
appear first.

---

**Project: Song Tool**
- Tagline: Music catalog and playlist builder for working musicians
- Live URL: https://haze-song-tool.vercel.app
- Stack tags: Next.js 16, TypeScript, Supabase, Drizzle ORM, Vercel
- Description: Full-stack music catalog and playlist builder. Users log songs with metadata
  (BPM, key, chord progressions, lyrics, streaming links), filter by any combination of
  fields, and save results as named playlists with drag-and-drop ordering. Built with Next.js
  16 App Router, TypeScript end-to-end, Supabase (PostgreSQL + auth), Drizzle ORM, and
  deployed on Vercel. Key technical decisions: JWT cookie sessions validated server-side on
  every request, PostgreSQL tsvector generated column for full-text lyric search, fractional
  position indexing for drag-and-drop reordering with single-row updates, and defense-in-depth
  auth enforced at both page layout and API route layers. End-to-end tested with Playwright.
- Category badge: "Full-Stack"

---

**Project: Workout App**
- Tagline: Account-based fitness tracker with structured 8-week program
- Live URL: https://workout.hazelugo.com
- Stack tags: JavaScript, Supabase, Vercel, Google OAuth
- Description: Started as a static local workout viewer and evolved into a multi-user
  account-based application. Implements email/password and Google OAuth authentication,
  per-user data isolation with row-level security in Supabase, protected route logic, and
  a custom onboarding flow stored to user profile. Vercel SPA routing configured to handle
  OAuth redirects without 404s. The evolution from localStorage to authenticated per-user
  PostgreSQL storage is documented and demonstrates applied understanding of auth
  architecture and production deployment configuration.
- Category badge: "Full-Stack"

---

**Project: Emma's Math Quest**
- Tagline: Minecraft-themed adaptive math game for a 6-year-old
- Stack tags: Vue 3, Vite, Tailwind CSS v4, Web Audio API
- Description: Mobile-first math game built with Vue 3, Vite, and Tailwind CSS v4. Features
  adaptive difficulty via a rolling 10-answer window targeting 80% success rate, synthesized
  audio effects via Web Audio API (no external files), CSS confetti animations on correct
  answers, and full accessibility compliance including prefers-reduced-motion support. All
  buttons meet minimum 60px touch target size. Built for a real user with real constraints —
  not a demo.
- Category badge: "Frontend"

---

### 4. Add a new "How I Work" section

This is the most important new section. It does not exist on the current site and is the
primary differentiator for the AI integration audience.

**Section ID:** `#workflow`
**Nav label:** "Workflow"
**Position:** Insert between Skills and Projects in the sidebar nav and page flow

**Content to communicate:**

The section explains the AI-assisted development workflow in concrete terms. It is not a
list of tools. It tells the story of how a project actually gets built.

The three phases to describe:

**Phase 1 — Spec & Planning (GSD)**
GSD (Get Shit Done) is a meta-prompting, context engineering, and spec-driven development
system for Claude Code with 58k GitHub stars. Before writing a line of code, GSD runs a
structured discovery process: it asks questions until it fully understands the project
(goals, constraints, edge cases), spawns parallel research agents to investigate the domain,
extracts v1/v2 requirements, and produces a roadmap. Each phase then runs discuss → plan →
execute → verify with fresh context windows per task to prevent context rot. The output is
atomic git commits per task, a clean git history, and `.planning/` markdown files that serve
as persistent project memory across sessions.

**Phase 2 — Build (Claude Code + MCPs)**
Development happens in VS Code terminal using Claude Code as the primary coding agent, with
MCP servers wired in for Supabase (database operations), Gemini (second-opinion reasoning),
and Claude-native tools. Multiple AI systems are orchestrated simultaneously, not used
sequentially. Context across sessions is managed via structured markdown files —
PROJECT.md, REQUIREMENTS.md, STATE.md, ROADMAP.md — so no session starts cold.

**Phase 3 — Quality Gate (Impeccable)**
Before shipping, every UI goes through Impeccable — a 23-command design intelligence system.
The `/teach` command first profiles the target audience, register, and voice. Then `/audit`
runs a five-dimension technical quality check across accessibility, performance, theming,
responsive design, anti-patterns, and design consistency, with P0-P3 severity ratings and
specific line-number references. Individual commands (`/adapt`, `/polish`, `/harden`,
`/typeset`, `/optimize`) then resolve each finding in focused passes. This is the quality
gate that separates shipped work from production-ready work.

**Visual treatment suggestion:**
Three numbered steps with a short label and 2-3 sentence description each. Use the existing
section heading pattern. No icons. Consistent with the rest of the site's flat, typographic
aesthetic.

---

### 5. Add /resume route

Add a linked page at `/resume` (or a `resume.html` file at root) that renders a clean,
printable version of the cybersecurity resume. This page should:
- Be minimal — white background, black text, no sidebar
- Contain the full resume content from the updated Cyber_Resume.md
- Have a "Download PDF" link pointing to the existing `resume.pdf`
- Link back to the main site
- Be linked from the main site footer and contact section

---

## What Not To Change

- The design system — OKLCH tokens, typography pairing, color palette
- The accordion pattern for projects
- The sidebar navigation structure (extend it, don't replace it)
- The vanilla JS / no-framework approach
- The single-file architecture (keep everything in `index.html` plus `resume.html`)
- The existing work history section content (update dates/status only)
- The existing security/network lab projects (keep all five, just add the new ones above them)

---

## Content & Voice Notes

- First person throughout — "I built", "I configured", not passive voice
- Specific over generic — name the tools, the stack, the decisions, not just the outcomes
- The bilingual angle matters — Hector is fluent English/Spanish, based in Mission TX (RGV)
- Do not use "passionate", "enthusiastic", "leverage", or "utilize"
- The tone on the existing site is direct, technical, and confident without being arrogant —
  match it exactly
- The AI integration content should read as a natural extension of the security/network
  identity, not a pivot. The through-line is: someone who builds and defends systems with
  rigor.

---

## Technical Constraints

- Single HTML file (`index.html`) plus a new `resume.html`
- No npm, no build step, no framework
- All CSS in `<style>` block in the same file
- All JS in `<script>` block at the bottom of the same file
- External resources: Google Fonts only (already loaded)
- Must pass Impeccable audit after changes — run `/impeccable audit` when complete
- Must work without JavaScript (core content readable, nav degrades gracefully)

---

## Definition of Done

- [ ] All critical and high audit issues resolved
- [ ] Degree status updated to completed throughout
- [ ] Three new AI projects added to accordion
- [ ] "How I Work" section live with three-phase workflow description
- [ ] Skills section updated with AI development category
- [ ] Hero and about updated to reflect dual-track identity
- [ ] `/resume` page live and linked from main site
- [ ] Site passes a follow-up `/impeccable audit` with no critical or high findings
- [ ] All existing five security/network projects still present and functional
- [ ] Mobile layout verified on 390px viewport for all new and modified sections

---

## How To Use This Brief

1. Open Claude Code in your portfolio project directory
2. Run `/gsd-new-project`
3. When GSD asks what you want to build, paste this document or reference it
4. GSD will run its discovery phase — answer any clarifying questions it asks
5. Approve the roadmap it produces
6. Run the discuss → plan → execute → verify loop per phase
7. After execution, run `/impeccable audit` to verify quality gate
8. Run individual Impeccable commands to resolve any new findings
