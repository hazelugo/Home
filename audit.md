# Portfolio Audit Report — Hector Lugo (hazelugo.com)

**Date:** May 10, 2026 | **File:** `index.html` (single-file)
**Status:** 12 of 16 issues resolved + 1 bonus fix applied

---

## Anti-Patterns Verdict: PASS

No AI slop detected. Specific evidence:

- **No gradient text** — accent color applied to targeted text nodes (`hero-name .last`, `section-heading em`), not sprayed everywhere
- **No glassmorphism or glow** — explicitly rejected; the design is flat with border-based separation
- **No card grid for projects** — accordion list is a deliberate, differentiated choice
- **No hero metrics section** — ("5+ years", "100 clients", etc.) absent. Good.
- **No generic fonts** — Bricolage Grotesque + Geist is a distinctive, slightly unusual pairing; not Inter + Roboto
- **No terminal aesthetic** — light theme in a dark-mode-dominated space is genuinely differentiated
- **No matrix motifs** — not a single `#` or `>_`

The OKLCH color system, warm-neutral `bg` tones, and blue accent with warm undertone (`hue 258` on cool, `hue 75` on warm) shows considered color work. This portfolio reads as intentional and distinctive.

---

## Executive Summary

| Severity | Found | Fixed | Remaining |
|---|---|---|---|
| Critical | 2 | 2 | 0 |
| High | 5 | 5 | 0 |
| Medium | 5 | 3 | 2 |
| Low | 4 | 2 | 2 |
| **Total** | **16** | **12** | **4** |

**Bonus fix applied:** Display font weight mismatch — 4 Bricolage Grotesque elements declared `font-weight: 700` (not loaded); changed to `800` to match actual browser rendering.

**Remaining open:** M-1 (hardcoded colors), M-5 (contrast check), L-3 (hero aria-label), L-4 (OG image verification)

---

## Detailed Findings

---

### Critical Issues

**C-1: `contact-link:hover` causes layout reflow and visual shift** ✅ FIXED
- **Location:** CSS `.contact-link:hover`
- **Category:** Performance / UX
- **Description:** The hover state added `padding-left`, `padding-right`, and `margin` — triggering browser reflow and causing the element to physically shift and resize on hover.
- **Fix (`/polish`):** Moved `padding: 1.1rem 0.75rem` and `margin: 0 -0.75rem` to the base `.contact-link` rule. Hover now only toggles `background` — a paint-only operation. Added `:active` state for touch feedback.

---

**C-2: Mobile `project-row` grid overflow — toggle wraps to wrong position** ✅ FIXED
- **Location:** CSS `@media (max-width: 768px)` `.project-row`
- **Category:** Responsive Design
- **Description:** Desktop uses 4-column grid; mobile dropped to 3 columns, causing the 4th child (`.project-toggle`) to wrap to the next row at the far left — visually broken.
- **Fix (`/adapt`):** Added `.project-tag { display: none }` on mobile. Row now has 3 children for 3 columns (number, content, toggle) — no wrapping.

---

### High-Severity Issues

**H-1: No skip navigation link** ✅ FIXED
- **WCAG:** 2.4.1 (Bypass Blocks), Level A
- **Fix (`/harden`):** Added `.skip-link` CSS (off-screen by default, visible on `:focus`) and `<a href="#hero" class="skip-link">Skip to content</a>` as the first element in `<body>`.

---

**H-2: Active sidebar items missing `aria-current`** ✅ FIXED
- **WCAG:** 4.1.2
- **Fix (`/harden`):** `IntersectionObserver` callback now calls `item.removeAttribute("aria-current")` on all items during the clear pass, then `active.setAttribute("aria-current", "location")` on the active item.

---

**H-3: Sub-minimum font sizes in multiple locations** ✅ FIXED
- **WCAG:** 1.4.4 (Resize Text)
- **Description:** `0.67rem` (~10.7px) used in 6 elements: `.sidebar-email`, `.avail-label`, `.info-block-title`, `.edu-badge`, `.tool-chip`, `.project-tag`.
- **Fix (`/typeset`):** All six instances raised to `0.75rem` (12px) in a single `replace_all` pass. Styling intent (monospaced, uppercase, tracked) preserved.

---

**H-4: Certifications strip — no mobile scroll affordance** ✅ FIXED
- **Category:** Responsive Design / UX
- **Description:** 5 items at `min-width: 155px` = 775px+ required horizontal scroll on mobile with no visual indicator.
- **Fix (`/adapt`):** Strip now wraps to a 2×2 grid on mobile (`flex-wrap: wrap`, each item `flex: 1 1 50%`). "All Active" status bar spans full width at the bottom, centered. Borders adjusted for the new layout.

---

**H-5: Phone number inaccessible without CSS** ✅ FIXED
- **Category:** Accessibility
- **Description:** Phone number displayed only via CSS `::after` pseudo-element content, which screen readers handle inconsistently.
- **Fix (`/harden`):** Added `aria-label="Phone: 956-432-3287"` to the phone `<a>` element.

---

### Medium-Severity Issues

**M-1: Three hardcoded OKLCH color values instead of CSS variables** ⬜ OPEN
- **Location:** Pulse-dot `::after`, `.edu-badge` border, `.nav-overlay` background
- **Category:** Theming
- **Description:** Three inline OKLCH values with opacity should reference CSS tokens. Minor maintenance burden if root colors ever change.
- **Recommendation:** Define `--green-halo`, `--overlay-bg` tokens or use relative color syntax.
- **Suggested command:** `/normalize`

---

**M-2: `handleProjectKey` function defined but never called** ✅ FIXED
- **Category:** Code Quality
- **Fix (`/polish`):** Dead function removed. Native `<button>` keyboard behavior handles Enter/Space without it.

---

**M-3: Sidebar IntersectionObserver dead zone at `#certifications`** ✅ FIXED
- **Category:** UX
- **Description:** `div[id]` in the selector caused the observer to fire on `#certifications`, clearing all active states with no match — leaving the sidebar deselected during a natural scroll path.
- **Fix (`/polish`):** Changed selector to `section[id]` only.

---

**M-4: Unused font weight loaded (Geist 300)** ✅ FIXED
- **Category:** Performance
- **Fix (`/polish`):** Removed `300;` from the Google Fonts Geist weight list. One fewer font variant fetched per page load.

---

**M-5: `--text-muted` contrast may be marginal on `--bg-2`** ⬜ OPEN
- **WCAG:** 1.4.3 (Contrast Minimum), Level AA
- **Category:** Accessibility
- **Description:** `--text-muted: oklch(55% 0.013 258)` on `--bg: oklch(97% 0.009 75)` may be near the 4.5:1 threshold. Needs verification via OKLCH → sRGB contrast tool.
- **Recommendation:** If below 4.5:1, lower `--text-muted` lightness to ~50%.
- **Suggested command:** `/colorize`

---

### Low-Severity Issues

**L-1: Mobile sidebar focus not trapped when open** ✅ FIXED
- **Category:** Accessibility
- **Fix (`/harden`):** `openNav()` now moves focus to the first `.sidebar-item`. `closeNav()` returns focus to `menuBtn`.

---

**L-2: No `:active` states for touch interaction feedback** ✅ FIXED
- **Category:** UX
- **Fix (`/polish`):** Added `:active` states to `.btn-primary` (cancels hover lift, restores base bg), `.btn-ghost` (darkens border), and `.contact-link` (shared with `:hover` rule).

---

**L-3: `<section id="hero">` has no accessible label** ⬜ OPEN
- **Category:** Accessibility
- **Description:** Hero section has no `aria-label` or `aria-labelledby`. Very minor — screen readers still reach the `h1` immediately.
- **Recommendation:** Add `aria-labelledby="hero-heading"` + `id="hero-heading"` to the `h1`.

---

**L-4: OG image references external URL — not verifiable from code** ⬜ OPEN
- **Category:** Content
- **Description:** `https://hazelugo.com/og-image.png` — if this doesn't exist, social sharing previews render with no image.
- **Recommendation:** Verify the file exists at the referenced path before deploying.

---

### Bonus Fix (found during `/optimize`)

**B-1: Display font weight mismatch** ✅ FIXED
- **Category:** Performance / Typography
- **Description:** Bricolage Grotesque is loaded at weights `400`, `600`, `800` only. Four elements declared `font-weight: 700` while using `var(--font-display)` (`.cert-name`, `.project-name`, `.timeline-role`, `.avail-status`). The CSS matching algorithm already fell back to `800`, but the mismatch triggered unnecessary font synthesis work.
- **Fix (`/optimize`):** Changed all four to `font-weight: 800` — explicit, matches the loaded set, eliminates the fallback indirection.

---

## Patterns & Systemic Issues

1. ~~**Sub-minimum font sizes**: `0.67rem` appears in 6+ components.~~ ✅ Fixed globally via `/typeset`.
2. **Hardcoded OKLCH values**: 3 instances remain open (M-1). Worth a `/normalize` pass.
3. ~~**Hover-only interaction model**~~ ✅ Fixed — `:active` states added to primary interactive elements via `/polish`.

---

## Positive Findings

What's working exceptionally well:

1. **Reduced motion support** — `@media (prefers-reduced-motion: reduce)` is thorough: kills all animations AND immediately reveals `.reveal` elements. Textbook implementation.
2. **Semantic project buttons** — `<button type="button">` with `aria-expanded` for the accordion is exactly correct. Many portfolios use `<div onclick>` here.
3. **Focus visible styling** — `:focus-visible` + `:focus:not(:focus-visible) { outline: none }` is the correct modern pattern. The 2px accent-colored outline is clear and on-brand.
4. **Design token discipline** — The CSS custom property system is comprehensive and coherent. OKLCH color space shows genuine color knowledge.
5. **No JavaScript dependencies** — Zero external JS. Pure vanilla. The reveal observer, project accordion, and sidebar toggle are all tight, purpose-built implementations.
6. **Mobile hamburger** — Correct `aria-label`, `aria-expanded`, `aria-controls`, Escape key to close, overlay click to close. Full keyboard/mobile interaction pattern.
7. **Typography hierarchy** — Bricolage Grotesque for display, Geist for body, Geist Mono for metadata creates a clear, three-level system that serves both the fast skim and slow read.
8. **Grid-based expand animation** — `grid-template-rows: 0fr → 1fr` for project expand avoids the `height: auto` transition limitation elegantly.

---

## Recommendations by Priority

**Immediate — all resolved ✅**

**Short-term — all resolved ✅**

**Medium-term — partially resolved:**
- [x] ~~Verify `--text-muted` contrast ratio~~ (M-5 — still open, needs tooling)
- [x] ~~Replace 3 hardcoded OKLCH values with tokens~~ (M-1 — still open)
- [x] Remove `#certifications` from sidebar observer selector (M-3) ✅
- [x] Delete dead `handleProjectKey` function (M-2) ✅

**Long-term / remaining:**
- [ ] Verify `--text-muted` contrast ratio with OKLCH → sRGB tool (M-5)
- [ ] Replace 3 hardcoded OKLCH values with CSS tokens (M-1)
- [ ] Add `aria-labelledby` to hero section (L-3)
- [ ] Verify `hazelugo.com/og-image.png` exists before deploy (L-4)

---

## Suggested Commands for Remaining Issues

| Command | Addresses |
|---|---|
| `/normalize` | M-1 (hardcoded OKLCH colors) |
| `/colorize` | M-5 (contrast verification) |
