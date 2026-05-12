---
phase: 03-resume-page-quality-gate
plan: 01
subsystem: index.html
tags: [cta, og-meta, resume-links, footer, contact]
dependency_graph:
  requires: []
  provides: [resume-links-wired, og-url-meta, corrected-cta-text]
  affects: [index.html]
tech_stack:
  added: []
  patterns: [contact-link pattern replicated for resume row]
key_files:
  modified:
    - index.html
decisions:
  - Hero CTA changed from "View Lab Work" to "View Projects" to match actual section heading
  - og:url inserted between og:type and og:image matching existing 4-space indentation
  - Footer resume link added as plain <a> sibling after mailto link
  - Document SVG icon used for resume contact-link row (standard file/page icon paths)
metrics:
  duration: ~10 minutes
  completed: 2026-05-11
  tasks_completed: 2
  tasks_total: 2
  files_modified: 1
---

# Phase 03 Plan 01: Index.html Carry-over Fixes Summary

Four targeted fixes applied to index.html: corrected hero CTA text, added missing og:url meta, wired footer resume link, and added 5th contact-link row linking to resume.html.

## Tasks Completed

| Task | Name | Commit | Files |
|------|------|--------|-------|
| 1 | Fix hero CTA text and add og:url meta tag | e19bf2a | index.html |
| 2 | Add resume link to footer and new contact-link row | 0e68f2d | index.html |

## What Was Built

**Task 1 — CTA + og:url:**
- Hero button text changed from "View Lab Work" to "View Projects" (line 1285); href, SVG, and class unchanged
- `<meta property="og:url" content="https://hazelugo.com/" />` inserted at line 20, between og:type and og:image

**Task 2 — Resume links:**
- Footer: `<a href="resume.html">View Resume</a>` added as 4th sibling after the mailto link
- Contact section: 5th `.contact-link` block appended after Phone row — document SVG icon, label "Resume", value "hazelugo.com/resume", href="resume.html"

## Verification Results

- `grep -c 'href="resume.html"' index.html` → `2` (footer + contact row)
- `grep -q 'View Projects' index.html` → PASS
- `grep -q 'View Lab Work' index.html` → PASS (not found — correctly absent)
- `grep -q 'og:url' index.html` → PASS

## Deviations from Plan

None - plan executed exactly as written.

## Known Stubs

None — all links point to real targets (resume.html will be created in plan 03-02; footer and contact rows are wired and ready).

## Threat Flags

None — no new network endpoints, auth paths, or trust boundary changes introduced. Static HTML link additions only.

## Self-Check: PASSED

- index.html modified: confirmed (git shows 2 commits with changes)
- Commit e19bf2a exists: confirmed
- Commit 0e68f2d exists: confirmed
- 2 occurrences of href="resume.html": confirmed
- "View Projects" present, "View Lab Work" absent: confirmed
- og:url present: confirmed
