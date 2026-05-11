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

**C-1: `contact-link:hover` causes layout reflow and visual shift** ✅ FIXED (`/polish`)
- **Location:** CSS `.contact-link:hover`
- **Category:** Performance / UX
- **Description:** The hover state added `padding-left: 0.75rem`, `padding-right: 0.75rem`, and `margin: 0 -0.75rem`. Changing `padding` and `margin` triggers browser layout (reflow), causing the element to physically shift and resize on hover.
- **Impact:** Visually jank — contact links jumped horizontally on hover. On touch devices, hover doesn't fire reliably so the tint reveal never triggered.
- **Fix:** Moved `padding: 1.1rem 0.75rem` and `margin: 0 -0.75rem` to the base `.contact-link` rule. Hover now only toggles `background` — a paint-only operation. Added `:active` state for touch feedback.

---

**C-2: Mobile `project-row` grid overflow — toggle wraps to wrong position** ✅ FIXED (`/adapt`)
- **Location:** CSS `@media (max-width: 768px)` `.project-row`
- **Category:** Responsive Design
- **Description:** Desktop uses `grid-template-columns: 2.25rem 1fr auto auto` (4 columns). Mobile dropped to 3 columns, causing the 4th child (`.project-toggle`) to wrap to the next row at column 1 — visually broken.
- **Impact:** On mobile, the +/− expand toggle appeared misaligned beneath the project number.
- **Fix:** Added `.project-tag { display: none }` on mobile. Row now has 3 children for 3 columns (number, content, toggle) — no wrapping.

---

### High-Severity Issues

**H-1: No skip navigation link** ✅ FIXED (`/harden`)
- **Location:** `<body>` opening, before `.sidebar`
- **WCAG:** 2.4.1 (Bypass Blocks), Level A
- **Category:** Accessibility
- **Description:** No skip link existed. Keyboard users had to Tab through all 7 sidebar items before reaching page content.
- **Fix:** Added `.skip-link` CSS (off-screen by default, visible on `:focus`, styled in accent blue) and `<a href="#hero" class="skip-link">Skip to content</a>` as the first element in `<body>`.

---

**H-2: Active sidebar items missing `aria-current`** ✅ FIXED (`/harden`)
- **Location:** JS sidebar active state observer
- **WCAG:** 4.1.2
- **Category:** Accessibility
- **Description:** `IntersectionObserver` added/removed the `active` CSS class but never set `aria-current` — screen readers had no way to know which section was active.
- **Fix:** Observer callback now calls `item.removeAttribute("aria-current")` on all items during the clear pass, then `active.setAttribute("aria-current", "location")` on the active item.

---

**H-3: Sub-minimum font sizes in multiple locations** ✅ FIXED (`/typeset`)
- **Location:** `.sidebar-email`, `.avail-label`, `.info-block-title`, `.edu-badge`, `.tool-chip`, `.project-tag`
- **WCAG:** 1.4.4 (Resize Text)
- **Category:** Accessibility
- **Description:** `0.67rem` at 16px base = ~10.7px — well below the 12px minimum for legibility.
- **Fix:** All six instances raised to `0.75rem` (12px) via a single `replace_all` pass. Styling intent (monospaced, uppercase, tracked) preserved.

---

**H-4: Certifications strip — no mobile scroll affordance** ✅ FIXED (`/adapt`)
- **Location:** `.certs-strip`, `#certifications` section
- **Category:** Responsive Design / UX
- **Description:** 5 items at `min-width: 155px` = 775px+ required horizontal scroll on mobile with no visual indicator.
- **Fix:** Strip now wraps to a 2×2 grid on mobile (`flex-wrap: wrap`, each item `flex: 1 1 50%`). "All Active" status bar spans full width at the bottom, centered. Borders adjusted for the new layout.

---

**H-5: Phone number inaccessible without CSS** ✅ FIXED (`/harden`)
- **Location:** Phone `<a>` in contact section
- **Category:** Accessibility
- **Description:** Phone number displayed only via CSS `::after` pseudo-element content, which screen readers handle inconsistently. The underlying div was empty.
- **Fix:** Added `aria-label="Phone: 956-432-3287"` to the phone `<a>` element.

---

### Medium-Severity Issues

**M-1: Three hardcoded OKLCH color values instead of CSS variables** ⬜ OPEN
- **Location:** Pulse-dot `::after` (line ~289), `.edu-badge` border (line ~611), `.nav-overlay` background (line ~1061)
- **Category:** Theming
- **Description:**
  - `background: oklch(52% 0.16 145 / 0.28)` — should reference `--green` with opacity
  - `border: 1px solid oklch(60% 0.14 65 / 0.4)` — should reference `--accent-2` with opacity
  - `background: oklch(17% 0.015 258 / 0.35)` — should reference `--text` with opacity
- **Impact:** If any root colors are updated, these three instances remain stale.
- **Recommendation:** Define `--green-halo`, `--overlay-bg` tokens or use relative color syntax.
- **Suggested command:** `/normalize`

---

**M-2: `handleProjectKey` function defined but never called** ✅ FIXED (`/polish`)
- **Category:** Code Quality
- **Description:** Dead function attached to nothing. Native `<button>` keyboard behavior handles Enter/Space without it.
- **Fix:** Function removed.

---

**M-3: Sidebar IntersectionObserver creates a dead zone at `#certifications`** ✅ FIXED (`/polish`)
- **Category:** UX
- **Description:** `div[id]` in the selector caused the observer to fire on `#certifications`, clearing all active sidebar states with no match — sidebar went deselected during a natural scroll path.
- **Fix:** Changed selector to `section[id]` only.

---

**M-4: Unused font weight loaded (Geist 300)** ✅ FIXED (`/polish`)
- **Category:** Performance
- **Description:** `font-weight: 300` appeared nowhere in the CSS. Light-weight Geist variant was being fetched and never used.
- **Fix:** Removed `300;` from the Google Fonts Geist weight list.

---

**M-5: `--text-muted` contrast may be marginal on `--bg-2`** ⬜ OPEN
- **Location:** `.about-text p`, `.project-detail-text`, `.timeline-bullets li`, `.hero-desc`
- **WCAG:** 1.4.3 (Contrast Minimum), Level AA
- **Category:** Accessibility
- **Description:** `--text-muted: oklch(55% 0.013 258)` on `--bg: oklch(97% 0.009 75)` may be near the 4.5:1 threshold. Needs verification via OKLCH → sRGB contrast tool.
- **Impact:** Users with imperfect vision or in bright-light environments may find body text difficult.
- **Recommendation:** Test with a contrast checker. If below 4.5:1, lower `--text-muted` lightness to ~50%.
- **Suggested command:** `/colorize`

---

### Low-Severity Issues

**L-1: Mobile sidebar focus not trapped when open** ✅ FIXED (`/harden`)
- **Category:** Accessibility
- **Description:** When sidebar opened, focus stayed on the hamburger button and keyboard users could tab through obscured background content.
- **Fix:** `openNav()` moves focus to the first `.sidebar-item`. `closeNav()` returns focus to `menuBtn`.

---

**L-2: No `:active` states for touch interaction feedback** ✅ FIXED (`/polish`)
- **Category:** UX
- **Description:** Interactive elements relied entirely on `:hover` — no feedback on touch devices.
- **Fix:** Added `:active` states to `.btn-primary` (cancels hover lift, restores base bg), `.btn-ghost` (darkens border), and `.contact-link` (shared with `:hover` rule).

---

**L-3: `<section id="hero">` has no accessible label** ⬜ OPEN
- **Location:** Hero section
- **Category:** Accessibility
- **Description:** No `aria-label` or `aria-labelledby`. Very minor — screen readers still reach the `h1` immediately.
- **Recommendation:** Add `aria-labelledby="hero-heading"` + `id="hero-heading"` to the `h1`.

---

**L-4: OG image references external URL — not verifiable from code** ⬜ OPEN
- **Location:** `<meta property="og:image">` and `<meta name="twitter:image">`
- **Category:** Content
- **Description:** `https://hazelugo.com/og-image.png` — if this file doesn't exist, social sharing previews render with no image.
- **Recommendation:** Verify the file exists at that path before deploying.

---

### Bonus Fix (found during `/optimize`)

**B-1: Display font weight mismatch** ✅ FIXED (`/optimize`)
- **Category:** Performance / Typography
- **Description:** Bricolage Grotesque is loaded at weights `400`, `600`, `800` only. Four elements declared `font-weight: 700` while using `var(--font-display)`: `.cert-name`, `.project-name`, `.timeline-role`, `.avail-status`. The CSS matching algorithm already fell back to `800`, but the mismatch triggered unnecessary font synthesis work.
- **Fix:** Changed all four to `font-weight: 800` — explicit, matches the loaded set, eliminates the fallback indirection.

---

## Patterns & Systemic Issues

1. ~~**Sub-minimum font sizes**: `0.67rem` in 6+ components.~~ ✅ Fixed globally via `/typeset`.
2. **Hardcoded OKLCH values**: 3 instances remain (M-1). Worth a `/normalize` pass.
3. ~~**Hover-only interaction model**~~ ✅ Fixed — `:active` states added to primary interactive elements.

---

## Positive Findings

1. **Reduced motion support** — `@media (prefers-reduced-motion: reduce)` kills all animations AND immediately reveals `.reveal` elements. Textbook implementation.
2. **Semantic project buttons** — `<button type="button">` with `aria-expanded` for the accordion is exactly correct.
3. **Focus visible styling** — `:focus-visible` + `:focus:not(:focus-visible) { outline: none }` is the correct modern pattern. The 2px accent-colored outline is clear and on-brand.
4. **Design token discipline** — Comprehensive CSS custom property system. OKLCH color space shows genuine color knowledge.
5. **No JavaScript dependencies** — Zero external JS. Pure vanilla. All interactions are tight, purpose-built implementations.
6. **Mobile hamburger** — Correct `aria-label`, `aria-expanded`, `aria-controls`, Escape key to close, overlay click to close.
7. **Typography hierarchy** — Bricolage Grotesque / Geist / Geist Mono creates a clear three-level system.
8. **Grid-based expand animation** — `grid-template-rows: 0fr → 1fr` avoids the `height: auto` transition limitation elegantly.

---

## Remaining Open Items

| ID | Issue | Command |
|---|---|---|
| M-1 | 3 hardcoded OKLCH color values | `/normalize` |
| M-5 | `--text-muted` contrast — needs tool verification | `/colorize` |
| L-3 | Hero section missing `aria-labelledby` | manual |
| L-4 | OG image URL not verified | manual (pre-deploy) |
