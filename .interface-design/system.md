# Interface Design System — yessenov.github.io

## Domain Context

**Product:** Personal academic website for Murat Yessenov, Ph.D. — postdoctoral researcher in optics/photonics at Harvard SEAS.

**User:** Academic peers, hiring committees, collaborators, students. Arriving via Google Scholar, conference programs, or referrals. Scanning for credibility: affiliation, publication quality, research focus.

**Core Task:** Assess the researcher's profile and decide whether to reach out, cite, invite, or collaborate.

**Experience Quality:** Authoritative but approachable. Precise and unhurried — the feeling of a well-organized lab notebook. Not sterile like an institution page, not promotional like a startup.

---

## Palette

| Role | Value | Rationale |
|------|-------|-----------|
| Foundation | `#1a2744` (navy) | Depth, academia, trust — grounds the physical sciences domain |
| Foundation 2 | `#243560` (navy2) | Hover states, darkened accents |
| Accent | `#2e6da4` (steel blue) | Links and highlights — calm, not urgent |
| Text | `#222831` | Near-black, easier on eyes than pure black |
| Muted | `#5a6378` | Secondary text, metadata |
| Surface | `#f5f7fb` | Alternating section backgrounds — off-white, not clinical |
| Border | `#dde3ef` | Subtle separators |

Avoid: high-saturation colors, gradients, dark mode (not needed for academic audience).

---

## Typography

| Role | Font | Weight |
|------|------|--------|
| Headings | Lora (serif) | 600 |
| Body | Inter (sans-serif) | 300–500 |
| Metadata / labels | Inter | 600, uppercase, tracked |

Lora gives scholarly authority without stuffiness. Inter ensures legibility at small sizes for publication lists and CV entries.

---

## Layout

- Max content width: `900px`, centered
- Section padding: `5rem 2rem`
- Sticky nav: `56px` height, blur backdrop
- Alternating section backgrounds (white / `#f5f7fb`)
- Mobile breakpoint: `680px` — stacked layout, hamburger nav

---

## Component Patterns

**Social buttons:** Pill-shaped (`border-radius: 20px`), outlined by default, filled navy on hover. SVG icons inline. Never icon-only — always labeled.

**Research cards:** Bordered, `border-radius: 8px`, subtle lift on hover (`translateY(-2px)`). Diamond bullet icon in accent color.

**Publication list:** Venue label in uppercase accent color. Title in navy. Authors in muted. Inline tag-style links (Paper, DOI). Divider rows — no card wrapping, keeps it scannable.

**CV entries:** Two-column (`date | detail`), date column `min-width: 100px`. Category headers in small-caps accent.

**Buttons (primary):** Navy fill, `border-radius: 8px`, no shadow.

---

## Sections

1. **About** — photo + name + affiliation + bio + social links
2. **Research** — intro paragraph + 3-column card grid (placeholders until research directions finalized)
3. **Publications** — selected list + Google Scholar link
4. **CV** — positions → education → awards + PDF download
5. **Contact** — 2-column: address/email | links

---

## Decisions Log

| Date | Decision | Reason |
|------|----------|--------|
| 2026-06-02 | Single-page layout with anchor nav | Academic visitors scan sections; multi-page adds friction |
| 2026-06-02 | Lora serif for headings | Scholarly tone, matches physical sciences context |
| 2026-06-02 | No hero image/banner | Content credibility comes from text, not visuals |
| 2026-06-02 | Photo as circle, not rectangle | Warmer/approachable; standard for academic profiles |
| 2026-06-02 | Research cards marked as placeholders | Research classification not yet decided by user |
| 2026-06-02 | Added real Google Scholar URL, fixed LinkedIn slug, added DOIs to all 5 papers, corrected 3 wrong journal venues, corrected author list on Veiled Talbot and Anomalous Refraction, added publication years, removed stale pub-note | All were factual errors discoverable via web search |
