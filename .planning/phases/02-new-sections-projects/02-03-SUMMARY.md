---
phase: 02-new-sections-projects
plan: "03"
subsystem: index.html
tags: [projects-section, accordion, ai-projects, renumbering, external-links]
dependency_graph:
  requires:
    - "02-01 (tag-fullstack / tag-frontend CSS tokens required by new project tags)"
    - "02-02 (Workflow section inserted above Projects — DOM order context)"
  provides:
    - "Three new <button class='project-item'> accordion entries: Song Tool (01), Workout App (02), Emma's Math Quest (03)"
    - ".project-links CSS rules for View live / GitHub anchor row"
    - "Eight-item Projects accordion numbered 01..08 in DOM order"
  affects:
    - "Phase 2 complete — all PROJ-01..05, WKFL-01..04, NAVM-01..02 now satisfied"
tech_stack:
  added: []
  patterns:
    - "Exact .project-item accordion pattern reused — no new JS required"
    - ".project-links row inserted between .project-detail-text and .project-tools per D-16"
    - "Reveal stagger: reveal / reveal-d1 / reveal-d2 for the three new entries"
    - "All external links use target=_blank rel=noopener noreferrer per D-19"
key_files:
  created: []
  modified:
    - index.html
decisions:
  - "Honored CONTEXT.md D-18 over REQUIREMENTS.md PROJ-03 — Emma's Math Quest includes both live URL and GitHub (locked decision supersedes earlier requirement draft)"
  - "First-person grounded prose written from D-23/D-24/D-25 reference material — not verbatim copy, no 'passionate', no 'leverage'"
  - "Song Tool chip uses Next.js 16 (matches plan spec) not Next.js 15 (CONTEXT.md D-23 typo)"
metrics:
  duration_minutes: 15
  completed_date: "2026-05-11"
  tasks_completed: 3
  tasks_total: 3
  files_modified: 1
---

# Phase 02 Plan 03: New AI Project Accordion Entries Summary

Three new AI project accordion entries (Song Tool, Workout App, Emma's Math Quest) added above the five existing security/network labs in the Projects section, with a new .project-links CSS rule for the View live / GitHub anchor row, and the five existing labs renumbered 04-08 so the full list reads 01..08 in DOM order.

## Tasks Completed

| Task | Name | Commit | Files |
|------|------|--------|-------|
| 1 | Add .project-links CSS rule for the new external-link row | e1e7fc8 | index.html |
| 2 | Insert three new AI project accordion entries at top of projects-list | 350d18e | index.html |
| 3 | Renumber the five existing security/network project-num spans to 04-08 | 541f50a | index.html |

## Decisions Made

- Honored CONTEXT.md D-18 (locked decision) over REQUIREMENTS.md PROJ-03 for Emma's Math Quest — included both live URL (https://emath.hazelugo.com) and GitHub link. CONTEXT.md decisions were made after requirements were drafted and supersede.
- First-person grounded prose written for all three project descriptions from D-23/D-24/D-25 reference material. Voice: specific, no filler, no "passionate", no "leverage". Emma's description closes with "Built for a real user with real constraints — not a demo" per the CONTEXT.md specifics block.
- Song Tool chip labeled "Next.js 16" matching the plan spec (D-23 in CONTEXT.md reads "Next.js 15" but the plan task spec reads "Next.js 16" — plan spec takes precedence as the more recent artifact).

## Deviations from Plan

None — plan executed exactly as written.

## Known Stubs

None — all three projects are fully wired: descriptions are real prose (not placeholder), links point to real URLs, stack chips match the actual tech used.

## Threat Flags

None — no new network endpoints, auth paths, file access patterns, or schema changes introduced. All external links are outbound only (target=_blank).

## Self-Check: PASSED

- `.project-links {` in index.html: line 784, confirmed
- `.project-links a {` in index.html: line 790, confirmed
- `.project-links a:hover {` in index.html: line 798, confirmed
- Rules appear after `.project-detail-text` and before `.project-tools`: confirmed
- Song Tool project-num 01, line 1556: confirmed
- Workout App project-num 02, line 1595: confirmed
- Emma's Math Quest project-num 03, line 1633: confirmed
- Vulnerability Assessment Lab project-num 04, line 1671: confirmed
- SIEM Log Analysis Lab project-num 05, line 1713: confirmed
- Network Traffic Analysis project-num 06, line 1754: confirmed
- Segmented Home Network Lab project-num 07, line 1793: confirmed
- A/V Production LAN project-num 08, line 1834: confirmed
- Each number 01-08 appears exactly once in project-num spans: confirmed
- haze-song-tool.vercel.app present with target=_blank rel=noopener noreferrer: confirmed
- workout.hazelugo.com present with target=_blank rel=noopener noreferrer: confirmed
- emath.hazelugo.com present with target=_blank rel=noopener noreferrer: confirmed
- github.com/hazelugo/Song-Tool present: confirmed
- github.com/hazelugo/Workout-App present: confirmed
- github.com/hazelugo/EmmaApp present: confirmed
- tag-fullstack on Song Tool and Workout App: confirmed
- tag-frontend on Emma's Math Quest: confirmed
- All three new buttons carry onclick="toggleProject(this)" and aria-expanded="false": confirmed
- Commits e1e7fc8, 350d18e, 541f50a exist: confirmed
