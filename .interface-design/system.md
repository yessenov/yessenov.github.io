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
| 2026-06-02 | Removed "[Placeholder — research directions being finalized]" from all 3 research cards; tightened card prose and bio | Placeholder text signals an unfinished site to every visitor; the research directions were already clear enough to state confidently |
| 2026-06-02 | Bolded M. Yessenov in all publication author lines; added `.pub-authors strong` CSS rule | Universal academic convention; absence made the site look unpolished. Rule lifts the name to `--text` color against the muted author string. |
| 2026-06-02 | Added `.nav-links a.active` CSS rule (combined with `:hover`) | JS scroll-spy was already setting the class but no visual rule applied it — a silent broken feature. Active section nav item now stays highlighted while in view. |
| 2026-06-03 | Reordered publications newest-first (2026→2022→2020→2020→2019); moved year from author string into venue label ("Optica · 2026") | Newest-first is universal academic convention; the Harvard-era 2026 paper was buried at position 4. Year in venue line is in accent color — immediately scannable without hunting through the author string. |
| 2026-06-03 | Added one-sentence `.pub-teaser` to each publication, placed between title and authors | Bare citation lists read as a CV; teasers let non-expert visitors (hiring committees, cross-field collaborators) immediately grasp each paper's contribution. Pattern drawn from jonbarron.info and similar high-quality researcher sites. |
| 2026-06-04 | Added compact "News" section (3 items) between About and Research; added to nav | Top researcher sites (jonbarron.info, karpathy.ai, faculty pages) consistently use a news/updates feed to signal the site is actively maintained. Three verifiable items: 2026 Optica paper, 2025 Harvard appointment, 2022 AOP review. Added explicit `#research { background: var(--light) }` to preserve white-cards-on-off-white intent after nth-child parity shifted. |
| 2026-06-04 | Added ORCID iD (0000-0001-6850-1803) as social button (About) and link (Contact); used official ORCID SVG logo | ORCID is the standard persistent identifier for researchers — its absence is conspicuous on any academic profile. ID confirmed from orcid.org search result. Placed between LinkedIn and Email in the button row, follows convention from Harvard/MIT faculty pages. |
| 2026-06-04 | Replaced ♦ diamond icons on research cards with inline SVGs (lens cross-section, sine wave, atom orbital); updated `.card-icon` CSS from font-size to width/height for SVG sizing | Diamond was purely decorative noise with no semantic meaning. Lens, wave, and atom icons are immediately readable to any physicist and give each card a distinct visual identity. Same SVG-inline approach as social buttons. Tightened research intro from two sentences (incl. generic "I am broadly interested in…") to one specific sentence describing the actual research. |
| 2026-06-04 | Added descriptive `<title>`, `<meta name="description">`, Open Graph tags, Twitter Card tags, `<meta name="theme-color">`, `<link rel="canonical">`, and SVG favicon (navy circle, "MY" initials, data URI — no extra file needed) | The page title was bare "Murat Yessenov" with no other head metadata; search results showed no description, LinkedIn/Twitter shares had no rich preview, and the browser tab showed a blank icon. All fixable with ~10 head lines. |
| 2026-06-04 | Added `#publications { background: var(--white); }` to override nth-child-even on that section | Research and Publications were both `var(--light)` (#f5f7fb), making them visually merge on scroll. The nth-child alternation pattern broke when News was added. Publications on white also pairs well with the dense text content of a publication list. |
| 2026-06-04 | Moved `pub-teaser` to after `pub-authors` in all 5 publication entries; made teaser italic; reduced `pub-authors margin-bottom` from 0.5rem to 0.2rem; added `NEW` badge to Optica 2026 entry and `REVIEW` badge to AOP 2022 entry | Standard academic reading order is venue → title → authors → context — the previous teaser-before-authors order was non-conventional. Italic teaser visually distinguishes the "why care" sentence from the muted author string (both were the same color/size). Badges give hiring committees instant signal: `REVIEW` flags expert recognition (invited reviews require standing in field); `NEW` draws attention to the most recent paper without needing to scan dates. |
| 2026-06-05 | Added citation count ("2,500+ citations") to the publications section-intro, styled with `.stat-num` (navy, weight 600) so the metric pops against the muted context text | Verified via ResearchGate search result (2,523 citations as of 2026). Hiring committees and senior collaborators look for this signal immediately after seeing the paper count. The `stat-num` rule creates a three-level hierarchy in one line: navy numbers → muted text → accent link. Used "2,500+" as conservative lower bound that will always be true as citations grow. |
| 2026-06-05 | Added left-accent-border treatment to publication list: `border-left: 3px solid transparent` reserves space on all items (no hover layout shift); `var(--accent)` border appears on hover with a faint `rgba(245,247,251,0.55)` background tint; `.pub-featured` class keeps the border permanently on the 2026 Optica paper | All 5 pub items were visually identical with no interactive feedback. The persistent border on the featured paper creates immediate hierarchy ("here's what I'm working on now") — the same pattern used on jonbarron.info. Hover treatment on remaining papers gives the list a live, scannable feel without deviating from the palette. |
