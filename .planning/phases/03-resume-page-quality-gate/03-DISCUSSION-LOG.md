# Phase 3: Resume Page & Quality Gate - Discussion Log

> **Audit trail only.** Do not use as input to planning, research, or execution agents.
> Decisions are captured in CONTEXT.md — this log preserves the alternatives considered.

**Date:** 2026-05-11
**Phase:** 03-resume-page-quality-gate
**Areas discussed:** resume.html content, resume.html link placement, Carry-over quality fixes

---

## resume.html Content

| Option | Description | Selected |
|---|---|---|
| Cybersecurity/network only | Resume = professional IT doc; AI work at index.html | ✓ |
| Dual-track — everything | Include AI dev work and apps | |

**Sections:** Work history, Education, Certifications, Skills (all selected)

| Option | Description | Selected |
|---|---|---|
| Brief mention only | One line for AI development breadth | ✓ |
| No — keep focused | No AI mention at all | |
| Full AI section | Dedicated section for shipped apps | |

| Option | Description | Selected |
|---|---|---|
| Minimal browser default + print CSS | System font, @media print hides actions. Fast, print-ready. | ✓ |
| Match index.html fonts | Load Geist + Bricolage | |
| Pure HTML, no CSS | Browser default entirely | |

---

## resume.html Link Placement

| Option | Description | Selected |
|---|---|---|
| Add "View Resume" as 4th footer item | Simple text link alongside email | ✓ |
| Replace location text | Swap location for resume link | |
| Don't link from footer | Contact section only | |

| Option | Description | Selected |
|---|---|---|
| Add a contact-link row | Match Email/LinkedIn/GitHub/Phone pattern | ✓ |
| Second ghost button alongside Download | Pair with existing Download button | |
| Replace PDF link with resume.html | Fewer direct PDF links | |

---

## Carry-over Quality Fixes

| Option | Description | Selected |
|---|---|---|
| Change to "View Projects" | Accurate for current content mix | ✓ |
| Keep "View Lab Work" | Accept the mismatch | |
| Change to "View My Work" | More neutral | |

| Option | Description | Selected |
|---|---|---|
| Yes — add og:url | Add canonical URL tag | ✓ |
| Skip it | Leave for later | |

---

## Claude's Discretion

- Exact one-line AI development mention in resume.html
- Document structure / heading hierarchy for resume.html
- Document icon SVG for the new contact-link row

## Deferred Ideas

None.
