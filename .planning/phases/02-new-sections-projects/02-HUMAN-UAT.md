---
status: partial
phase: 02-new-sections-projects
source: [02-VERIFICATION.md]
started: 2026-05-11
updated: 2026-05-11
---

## Current Test

awaiting human testing

## Tests

### 1. Section background alternation
expected: Opening index.html in a browser, the sections alternate between plain (--bg) and tinted (--bg-2) backgrounds: About=tinted, Skills=plain, Workflow=tinted, Projects=plain, Experience=plain, Contact=plain. No two adjacent sections that share the same background feel visually merged.
result: [pending]

### 2. Workflow nav active state
expected: Scrolling to the #workflow section causes the "Workflow" sidebar item to highlight (border-left accent, bg-3 background). Scrolling away deactivates it. The IntersectionObserver wiring works correctly.
result: [pending]

### 3. Project accordion expand/collapse
expected: Clicking any of the three new AI project entries (Song Tool, Workout App, Emma's Math Quest) opens the accordion detail section with description, project-links row (View live →, GitHub →), and tool chips. Clicking again collapses. Opening one closes any previously open entry.
result: [pending]

## Summary

total: 3
passed: 0
issues: 0
pending: 3
skipped: 0
blocked: 0

## Gaps
