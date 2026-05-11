# hazelugo.com — Portfolio Rebuild

## What This Is

A portfolio site rebuild for Hector Lugo (hazelugo.com). The site is live, deployed as a single `index.html` — no framework, no build step, vanilla HTML/CSS/JS. The goal is to evolve it from a cybersecurity/network resume page into a dual-track portfolio that leads with AI integration and development while retaining the cybersecurity/network credentials as a secondary track. The existing design system is strong and stays.

## Core Value

A recruiter or hiring manager in any of three tracks — AI development, cybersecurity, or network — should finish reading in under 5 minutes and think "this person knows exactly what they're doing."

## Requirements

### Validated

- ✓ Light-theme portfolio with OKLCH color system, Bricolage Grotesque + Geist typography — existing
- ✓ Sidebar navigation with scroll-linked active state — existing
- ✓ Five security/network lab projects in accordion pattern — existing
- ✓ Work history timeline (Mission CISD, Charter Communications) — existing
- ✓ Contact section with email, LinkedIn, GitHub, phone — existing
- ✓ Accessibility: skip link, aria-current, focus management, reduced motion support — Phase 0 (audit fixes)
- ✓ Hero subtitle: "AI, Security & Network Professional" — Phase 1
- ✓ Degree: "B.A.T. — Computer Information Technology" (no date qualifier) — Phase 1
- ✓ About section: AI development track paragraph added — Phase 1
- ✓ Skills: "AI Development & Integration" leads the skills table — Phase 1
- ✓ OG meta updated to dual-track identity — Phase 1

### Active

- [ ] Three new projects added to accordion (Song Tool, Workout App, Emma's Math Quest) above existing security labs
- [ ] "How I Work" section (Phase 1 → GSD, Phase 2 → Claude Code + MCPs, Phase 3 → Impeccable) between Skills and Projects in nav and page flow
- [ ] Section numbering updated throughout to account for new "Workflow" section
- [ ] `resume.html` created — printable cybersecurity resume, minimal, linked from footer and contact
- [ ] OG meta description updated to reflect dual-track identity
- [ ] Mobile layout verified at 390px for all new and modified sections

### Out of Scope

- npm, build tools, frameworks — single-file constraint, no build step
- Dark mode — light theme is the deliberate differentiator
- Redesigning the design system — extend only, do not replace
- Backend / server-side logic — static site only
- Rewriting existing security/network project content — keep as-is
- Rewriting work history content — keep as-is
- Adding more than one new HTML page (`resume.html` only)

## Context

**Existing site:**
- 1,935 lines, single `index.html`, deployed on current host
- All CSS in `<style>` block, all JS in `<script>` block at bottom
- Audit pass completed (May 10, 2026) — all critical and high issues resolved
- `index.backup.html` exists at root as a snapshot before this rebuild

**New projects to add:**
- Song Tool — full-stack music catalog/playlist builder (Next.js 16, TypeScript, Supabase, Drizzle ORM, Vercel) — live: https://haze-song-tool.vercel.app — repo: https://github.com/hazelugo/Song-Tool
- Workout App — account-based fitness tracker with Google OAuth (JavaScript, Supabase, Vercel) — live: https://workout.hazelugo.com — repo: https://github.com/hazelugo/Workout-App
- Emma's Math Quest — adaptive Minecraft-themed math game for a 6-year-old (Vue 3, Vite, Tailwind CSS v4, Web Audio API) — no live URL — repo: https://github.com/hazelugo/EmmaApp

**AI workflow to document in "How I Work":**
- Phase 1: GSD (58k GitHub stars) — meta-prompting, spec-driven development, parallel research agents, atomic git commits
- Phase 2: Claude Code + MCPs (Supabase MCP, Gemini MCP, Claude-native tools) — context managed via structured markdown
- Phase 3: Impeccable (23-command quality gate) — audit → targeted fix commands → production-ready

**Voice:**
- First person throughout — "I built", "I configured"
- Specific over generic — name tools, stacks, decisions
- No "passionate", "enthusiastic", "leverage", "utilize"
- Through-line: someone who builds and defends systems with rigor

## Constraints

- **Architecture**: Single `index.html` + new `resume.html` only — no other new files
- **Tech stack**: Vanilla HTML/CSS/JS — no npm, no build step, no framework
- **External resources**: Google Fonts only (already loaded)
- **Design system**: Preserve OKLCH tokens, typography pairing, color palette — extend only
- **Accessibility**: Must pass follow-up Impeccable audit with no Critical or High findings
- **Compatibility**: Must work without JavaScript (core content readable, nav degrades gracefully)

## Key Decisions

| Decision | Rationale | Outcome |
|---|---|---|
| Extend design system, don't redesign | Existing OKLCH + typography is strong and distinctive; redesign would lose the identity | — Pending |
| AI track leads, security/network is secondary | Dual-track positioning; AI roles are currently the higher-opportunity market | — Pending |
| "How I Work" is its own section, not folded into About | This is the primary differentiator for AI audience — needs prominence and space | — Pending |
| New projects appear above existing security labs | AI-first ordering for the new primary audience | — Pending |
| No live URL for Emma's Math Quest | It's a personal tool, not a deployed app — GitHub repo tells the story | — Pending |
| `resume.html` is a separate file, not a route | No server-side routing available; static file is the correct approach | — Pending |

## Evolution

This document evolves at phase transitions and milestone boundaries.

**After each phase transition** (via `/gsd-transition`):
1. Requirements invalidated? → Move to Out of Scope with reason
2. Requirements validated? → Move to Validated with phase reference
3. New requirements emerged? → Add to Active
4. Decisions to log? → Add to Key Decisions
5. "What This Is" still accurate? → Update if drifted

**After each milestone** (via `/gsd-complete-milestone`):
1. Full review of all sections
2. Core Value check — still the right priority?
3. Audit Out of Scope — reasons still valid?
4. Update Context with current state

---
*Last updated: May 10, 2026 after initialization*
