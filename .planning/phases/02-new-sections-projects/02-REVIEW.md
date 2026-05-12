---
phase: 02-new-sections-projects
reviewed: 2026-05-11T00:00:00Z
depth: standard
files_reviewed: 1
files_reviewed_list:
  - index.html
findings:
  critical: 0
  warning: 1
  info: 3
  total: 4
status: issues_found
---

# Phase 02: Code Review Report

**Reviewed:** 2026-05-11
**Depth:** standard
**Files Reviewed:** 1 (index.html — 2193 lines, single vanilla HTML/CSS/JS file)
**Status:** issues_found

## Summary

Phase 2 adds the `#workflow` section, three AI project accordion entries (Song Tool, Workout App, Emma's Math Quest), new CSS tag tokens (`--tag-fullstack-*`, `--tag-frontend-*`), sidebar nav Workflow insertion, and section renumbering (Projects=04, Experience=05, Contact=06).

The implementation is structurally correct: all section numbers are accurate, all sidebar `data-section` attributes match their target `id` values, the `sectionObserver` will pick up `#workflow` because it is a proper `<section>` element, the new tag tokens are defined and consumed correctly by `.tag-fullstack` and `.tag-frontend`, and all project accordions include `aria-expanded`, `type="button"`, and `toggleProject(this)` consistently across all eight entries.

One warning and three info items follow.

---

## Warnings

### WR-01: `#workflow` has no visual background contrast against `#skills` — two consecutive non-alt sections

**File:** `index.html:1512`
**Issue:** `#workflow` does not carry the `section-alt` class. Neither does `#skills` (line 1459). The two sections are adjacent and share the same `--bg` background, separated only by a `1px solid var(--border)` line. With the former section ordering (About→Skills→Projects→Experience→Contact), the alternating-background rhythm was: alt / plain / alt / plain / plain. After inserting `#workflow` between Skills and Projects the rhythm becomes: alt / plain / **plain** / alt / plain / plain — two consecutive plain-background sections running together visually.

CLAUDE.md principle at stake: "Fast scan, deep read — the hierarchy must work at both 5 seconds and 5 minutes." A recruiter skimming at speed may not register Skills and Workflow as distinct sections; the single border is low-contrast signal.

**Fix:** Add `section-alt` to either `#skills` or `#workflow` to restore visual separation. The lower-friction option is to add it to `#workflow` since it is the new section:

```html
<!-- line 1512 — change: -->
<section id="workflow" class="section">

<!-- to: -->
<section id="workflow" class="section section-alt">
```

This restores the alternating rhythm: About(alt) → Skills(plain) → Workflow(alt) → Projects(alt is already there, so consider swapping Projects to plain) → Experience(plain) → Contact(plain). Alternatively, remove `section-alt` from Projects and give it to Workflow so the alt sections stay visually distributed. Either way, two consecutive identical backgrounds should be resolved.

---

## Info

### IN-01: Hero primary CTA label "View Lab Work" now undersells the lead content

**File:** `index.html:1283-1284`
**Issue:** The primary CTA reads "View Lab Work" and links to `#projects`. Projects now opens with three shipped AI applications (Song Tool, Workout App, Emma's Math Quest) before the security/network labs. Calling them "lab work" is accurate for entries 04-08 but misrepresents entries 01-03, which are production deployments with live URLs. This is the highest-visibility action on the hero — a recruiter targeting AI roles may deprioritize it on the label alone.

**Fix:** Consider a label that covers both tracks, e.g. "View Projects" or "View Work". One-word change, no structural impact:

```html
View Projects
```

---

### IN-02: Inline `onclick` handlers on all eight project buttons will be blocked by any future CSP

**File:** `index.html:1553, 1590, 1628, 1667, 1710, 1749, 1789, 1829`
**Issue:** All eight `.project-item` buttons use `onclick="toggleProject(this)"`. `toggleProject` is assigned to the global scope. This pattern works in the current architecture (no build step, no CSP header) but is fragile: any `Content-Security-Policy: script-src 'self'` header — a natural next step if the site ever adds a server or security headers — will silently break all accordion interactivity with no error surfaced to the user.

**Fix:** No action needed now if the deployment remains static Vercel with no custom CSP. If CSP headers are added in the future, migrate to `addEventListener` bindings at DOMContentLoaded:

```js
document.querySelectorAll('.project-item').forEach(item => {
  item.addEventListener('click', () => toggleProject(item));
});
```

And remove the `onclick` attributes from all eight buttons.

---

### IN-03: `.skills-table` class reused on `#workflow` section wrapper — semantically misleading

**File:** `index.html:1518`
**Issue:** The workflow section uses `<div class="skills-table">` as its outer wrapper (identical to the skills section at line 1465). The class name `skills-table` implies skills-specific content. The `.skill-row` / `.skill-category` / `.skill-list` child classes carry the same naming mismatch. Functionally there is no bug — the grid layout applies correctly to workflow content — but the class names create confusion when reading or maintaining the markup.

**Fix:** No immediate action required; this is a naming convention issue only. If the layout pattern grows further (e.g., a fourth section reuses it), consider renaming to a generic class like `.data-table` or `.row-layout` and aliasing `.skills-table` for backward compatibility.

---

_Reviewed: 2026-05-11_
_Reviewer: Claude (gsd-code-reviewer)_
_Depth: standard_
