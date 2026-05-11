# CLAUDE.md — Empire/Home Portfolio

## Design Context

### Users
Two overlapping audiences who both visit this portfolio:
- **Recruiters / HR screeners** — scanning quickly, need instant credibility signals in the first 5 seconds
- **Hiring managers / technical leads** — reading more carefully, evaluating depth, real-world experience, and problem-solving

The design must work at both speeds: a fast skim should leave a strong impression; a slow read should reward it.

### Brand Personality
**Sharp. Grounded. Capable.**

- Sharp: precise, no filler, every element earns its place
- Grounded: real experience, real lab work — not aspirational fluff
- Capable: demonstrates competence without overselling; the work speaks

Emotional goal: the visitor should finish reading and think "this person knows exactly what they're doing."

### Aesthetic Direction
**Bold / confident — light theme**

- Light background, not dark — rare in cybersecurity portfolios and immediately distinctive
- Strong typographic hierarchy — display font used assertively, not decoratively
- Accent color used with restraint and intention, not scattered everywhere
- Asymmetric layouts and deliberate grid breaks over repetitive card grids
- No terminal aesthetics, no green-on-black, no matrix motifs
- No glassmorphism, no glow effects
- No generic dev portfolio energy

**Anti-references:**
- Generic cybersecurity portfolio: dark mode + green text + matrix rain
- Corporate HR page: stiff, impersonal, templated
- Over-designed: competing animations, decorative effects fighting for attention
- Template sites: interchangeable, no personality or point of view

### Design Principles
1. **Earn every element** — if it doesn't communicate something specific, remove it
2. **Typography does the heavy lifting** — scale, weight, and spacing are the primary design tools
3. **Restraint over decoration** — one strong accent is worth ten subtle ones
4. **Fast scan, deep read** — the hierarchy must work at both 5 seconds and 5 minutes
5. **Light and confident** — the palette should feel crisp and assured, not clinical or corporate

<!-- GSD:project-start source:PROJECT.md -->
## Project

**hazelugo.com — Portfolio Rebuild**

A portfolio site rebuild for Hector Lugo (hazelugo.com). The site is live, deployed as a single `index.html` — no framework, no build step, vanilla HTML/CSS/JS. The goal is to evolve it from a cybersecurity/network resume page into a dual-track portfolio that leads with AI integration and development while retaining the cybersecurity/network credentials as a secondary track. The existing design system is strong and stays.

**Core Value:** A recruiter or hiring manager in any of three tracks — AI development, cybersecurity, or network — should finish reading in under 5 minutes and think "this person knows exactly what they're doing."

### Constraints

- **Architecture**: Single `index.html` + new `resume.html` only — no other new files
- **Tech stack**: Vanilla HTML/CSS/JS — no npm, no build step, no framework
- **External resources**: Google Fonts only (already loaded)
- **Design system**: Preserve OKLCH tokens, typography pairing, color palette — extend only
- **Accessibility**: Must pass follow-up Impeccable audit with no Critical or High findings
- **Compatibility**: Must work without JavaScript (core content readable, nav degrades gracefully)
<!-- GSD:project-end -->

<!-- GSD:stack-start source:STACK.md -->
## Technology Stack

Technology stack not yet documented. Will populate after codebase mapping or first phase.
<!-- GSD:stack-end -->

<!-- GSD:conventions-start source:CONVENTIONS.md -->
## Conventions

Conventions not yet established. Will populate as patterns emerge during development.
<!-- GSD:conventions-end -->

<!-- GSD:architecture-start source:ARCHITECTURE.md -->
## Architecture

Architecture not yet mapped. Follow existing patterns found in the codebase.
<!-- GSD:architecture-end -->

<!-- GSD:skills-start source:skills/ -->
## Project Skills

No project skills found. Add skills to any of: `.claude/skills/`, `.agents/skills/`, `.cursor/skills/`, or `.github/skills/` with a `SKILL.md` index file.
<!-- GSD:skills-end -->

<!-- GSD:workflow-start source:GSD defaults -->
## GSD Workflow Enforcement

Before using Edit, Write, or other file-changing tools, start work through a GSD command so planning artifacts and execution context stay in sync.

Use these entry points:
- `/gsd-quick` for small fixes, doc updates, and ad-hoc tasks
- `/gsd-debug` for investigation and bug fixing
- `/gsd-execute-phase` for planned phase work

Do not make direct repo edits outside a GSD workflow unless the user explicitly asks to bypass it.
<!-- GSD:workflow-end -->

<!-- GSD:profile-start -->
## Developer Profile

> Profile not yet configured. Run `/gsd-profile-user` to generate your developer profile.
> This section is managed by `generate-claude-profile` -- do not edit manually.
<!-- GSD:profile-end -->
