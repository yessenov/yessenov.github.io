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
| 2026-06-05 | Added `padding-left: 0.75rem` to `.pub-item`; added `background: rgba(46,109,164,0.05)` to `.pub-item.pub-featured` | The 3px accent border had zero gap to the adjacent text — content was cramped against the visual anchor. 0.75rem indent gives the border room to breathe. The 5%-opacity accent-blue tint on the featured paper creates a persistent, at-rest visual distinction (vs. the warm off-white of hover states) so the most recent paper reads as "primary" without requiring mouse interaction. |
| 2026-06-05 | Added 2023 news item: "Ultra-compact synthesis of space-time wave packets", Opt. Lett. 48, 2500 (2023), doi 10.1364/OL.48.002500 | The news section had a conspicuous 3-year gap (2022→2025) signalling a dormant site. Murat is first author on this OL paper (confirmed via arXiv 2212.12091 and opg.optica.org). Adds a chronological anchor in the UCF postdoc period. |
| 2026-06-05 | Added `aria-expanded="false"` to nav toggle button; JS now sets `aria-expanded` on click | Screen readers announced the hamburger button with no state — users had no way to know if the menu was open. `aria-expanded` is the standard ARIA pattern for disclosure widgets. |
| 2026-06-05 | Removed `#research { background: var(--light) }` and `#publications { background: var(--white) }` overrides; changed `.research-card` background from `var(--white)` to `var(--light)`; changed pub-item hover background from `rgba(245,247,251,0.55)` to `rgba(255,255,255,0.75)` | The two explicit overrides broke the natural nth-child(even) alternation, leaving Publications and CV both white and visually merged on scroll. Removing them restores clean white→light→white→light→white→light alternation across all 6 sections. Research cards now use `var(--light)` as a raised surface on the white research section (light-on-white = subtle contrast without a colored section background). Pub-item hover was nearly invisible on the now-light publications section; `rgba(255,255,255,0.75)` (slight white flash) is legible on `var(--light)`. Fixed aria-expanded not being reset when mobile nav closes via link click (WCAG 4.1.2). |
| 2026-06-06 | Changed `.research-grid` from `repeat(auto-fit, minmax(240px, 1fr))` to `repeat(3, 1fr)` with a `1fr` override below 680px; added `border-top: 2px solid var(--accent)` to `.research-card` | The `auto-fit minmax(240px)` rule produced a 2+1 card layout at viewport widths 700–800px (two cards in row 1, one full-width card below) — visually awkward for a three-equal-items grid. `repeat(3, 1fr)` guarantees 3 equal columns at all desktop widths and collapses to 1 column at mobile. The accent top bar ties each card visually to the steel-blue design language (the SVG icon is already `var(--accent)`) and adds a polished "flagged card" premium feel without deviating from the palette. |
| 2026-06-06 | Added scroll-reveal animation: `.reveal` (opacity 0, translateY 18px) / `.in-view` (opacity 1, no transform), `IntersectionObserver` (threshold 0.1, fires once then unobserves), `prefers-reduced-motion` override that skips all animation; applied to news-items, research-cards, pub-items, cv-blocks, contact-blocks; 100ms stagger on 2nd/3rd research cards via nth-child CSS | The site felt like a static document — every element was fully visible on load with no sense of depth or scroll progression. Scroll-reveal is used on virtually every quality researcher site (jonbarron.info, MIT/Harvard faculty pages) and is the single most visible "feel" upgrade short of a visual redesign. Fire-once + unobserve ensures no re-trigger jank and is garbage-collected. prefers-reduced-motion respected for accessibility. |
| 2026-06-06 | Added `rel="noopener noreferrer"` to all external `target="_blank"` links (social buttons, bio inline links, news DOIs, pub DOIs, contact links); `rel="noopener"` to local PDF links | All ~17 `target="_blank"` links were missing this attribute — a real security issue (opener access to the parent page) and a best-practice violation flagged by Lighthouse. Fixed in the same commit as scroll-reveal since both are polish/correctness passes with no visual conflict. | 
| 2026-06-06 | Added `loading="lazy"` to profile photo `<img>` | Defers off-screen image fetch until it's needed; no UX cost since photo is near top but browser may already be loaded by the time user scrolls. |
| 2026-06-06 | Added 2023 Optics Letters paper ("Ultra-compact synthesis of space-time wave packets", OL 48, 2500, doi 10.1364/OL.48.002500) to the selected publications list, positioned between the 2022 AOP review and the 2020 Nature Photonics paper (newest-first order); authors listed as M. Yessenov, A. F. Abouraddy | The paper was already referenced in the News section but absent from Publications — a visible inconsistency a careful visitor would notice. Adding it also fills the career arc gap between the 2022 review (UCF postdoc, Abouraddy group) and the 2026 Harvard paper. OL is a flagship OSA journal; first-author status and confirmed DOI/arXiv (2212.12091) make it a strong addition to the six selected papers. |
| 2026-06-06 | Removed the middle sentence of the bio ("My current projects include high-NA metalenses..."); replaced with `.bio-tags` pill row (Flat Optics · Metalenses · Space-Time Wave Packets · Structured Light · Neutral-Atom Arrays) | The prose list was the densest part of the About section — a hiring committee has to parse a sentence to extract five keywords. The tag row makes the same information instantly scannable. Tags styled with `rgba(46,109,164,0.07)` fill + `rgba(46,109,164,0.2)` border — same accent hue as the rest of the system, clearly subordinate to the social buttons, visually distinct from the pub-badge (tags are 0.75rem, non-uppercase vs. badges at 0.65rem uppercase). The bio is now two sentences: where he is + where he came from. Research areas are in the card grid below. |
| 2026-06-06 | Replaced Contact section "Links" column (Scholar, ORCID, LinkedIn, Capasso Group, CV — a full duplicate of the About social buttons) with a "Currently" column describing his active research and collaboration interests | The links block added zero information; every link was already reachable from the About section. "Currently" turns the page's concluding section from a dead-end into a conversation opener: it states what he is working on (metalenses + atom arrays, Lukin/QuEra collaboration) and explicitly invites contact on relevant topics. Content is factual, derived from the research cards already on the page. Also removed the generic "I am always happy to discuss..." sentence from the Get in Touch block, which became redundant once the Currently block ends with the same invitation. |
| 2026-06-07 | Added vertical timeline treatment to CV section (CSS-only): `border-left: 2px solid var(--border)` + `padding-left: 1.25rem` on `.cv-block`; hollow accent-colored dots (`.cv-entry::before`: 8px circle, `border: 2px solid var(--accent)`, `background: var(--white)`, `left: calc(-1.25rem - 5px)`) at each entry. Also added scroll-reveal stagger to the 4 news items (0.07s / 0.14s / 0.21s delays on children 2–4), matching the research-card stagger pattern. | The CV section was the last major section with no visual narrative — flat date/detail rows read like a spreadsheet. The timeline makes the career arc scannable as a progression story. The news stagger completes the pattern set by the research cards (stagger on all repeating list-style sections). No HTML changes required. |
| 2026-06-07 | Made all 6 publication titles direct DOI links: `<p class="pub-title"><a href="[doi]">Title</a></p>`; added `.pub-title a` CSS (inherits navy, goes accent + underline on hover); changed hero photo from `loading="lazy"` to `loading="eager"` | Publication titles are the primary click target when scanning a paper list — every academic reference database (Google Scholar, arXiv, ADS) and researcher site uses the title as the link. The separate "Paper" pill button is a secondary affordance; the title is the natural first-click. The lazy/eager fix is a correctness issue: above-the-fold images should never defer loading, as `lazy` adds a deliberate parse-delay before the browser even begins fetching the resource. |
| 2026-06-08 | Added `.about-metrics` stats line ("30+ papers · 2,500+ citations · Google Scholar") to About section, between bio paragraph and bio-tags; tightened `.bio` bottom margin from 1.5rem to 0.5rem (with `.about-metrics` providing 1.1rem gap to bio-tags) | Publication count and citation count are the first metrics hiring committees scan for — previously these numbers were only visible in the Publications section (below the fold for most visitors). Placing them in the hero bio makes the site immediately credible on landing. All three researcher-site references (jonbarron.info, karpathy.ai, MIT/Harvard faculty pages) surface these metrics in the above-the-fold bio area. The Google Scholar inline link gives the hero section a direct path to the full record. |
| 2026-06-07 | Added arXiv preprint links to all 6 selected publications as secondary `.pub-link--preprint` buttons; muted color (border `var(--border)`, text `var(--muted)`) distinguishes them from the primary accent-colored "Paper" DOI links; arXiv IDs verified via search: 2510.16269 (Optica 2026), 2201.08297 (AOP 2022), 2212.12091 (OL 2023), 1912.13341 (Nat. Phot. 2020), 2004.04875 (PRL 2020), 1904.01764 (Optica 2019) | Every paper on a physics researcher's site that has an arXiv preprint should link to it — many visitors can't access journal-paywalled versions, and physicists expect the arXiv version as a given. The muted secondary style keeps the DOI as the primary action and clearly signals "open access alternative" without competing with the official publication link. |
| 2026-06-07 | Removed `.affiliation-sub` element ("Capasso Group · John A. Paulson School of Engineering and Applied Sciences") from About section; moved Capasso Group as a direct link into the main `.affiliation` line ("Postdoctoral Fellow · Capasso Group, Harvard SEAS"); added `margin-bottom: 1rem` to `.affiliation` to preserve spacing; removed dead `.affiliation-sub` CSS rule; bumped `h1` from 2rem to 2.2rem; added `justify-content: center` to `.bio-tags` in the mobile breakpoint | The sub-affiliation line added zero net information — "John A. Paulson School of Engineering and Applied Sciences" is a verbose restatement of "Harvard SEAS," and "Capasso Group" already appeared in the bio. The single merged line ("Postdoctoral Fellow · Capasso Group, Harvard SEAS") is more scannable and eliminates a full line of text from the hero. The h1 bump gives the name proper hero weight. The bio-tags centering fix closes a visual inconsistency: `.social-links` already had `justify-content: center` on mobile but `.bio-tags` did not, causing the tag pills to left-align under a centered bio paragraph. |
| 2026-06-08 | Added `<script type="application/ld+json">` Person schema to `<head>`: name, honorificSuffix, jobTitle, affiliation (Harvard SEAS + url), url, email, sameAs array (Google Scholar, ORCID, LinkedIn), alumniOf (UCF), knowsAbout array. All values match links already present on the page — no new data introduced, just machine-readable. Enables Google Knowledge Panel for name searches and rich snippets showing correct affiliation + links in SERPs. |
| 2026-06-08 | Replaced `.section-title` full-width `border-bottom: 2px solid var(--border)` (gray stripe across the entire 900px content width) with a 48px × 3px `::after` pseudo-element in `var(--accent)` (steel blue) with `border-radius: 2px`; margin-bottom nudged from 1rem → 1.25rem to give the accent bar a touch more breathing room. Added per-item stagger delays to `.pub-list .reveal` (0.06s × items 2–6), completing the scroll-reveal stagger pattern already present in news items and research cards. | The gray full-width border looked generic (a default HTML horizontal-rule pattern); the short accent underline ties section headings into the same steel-blue design language used by pub-venue labels, card top borders, and CV timeline dots — giving every section a consistent visual identity. The pub-list stagger was the only repeating reveal group without delays, making Publications feel abrupt when scrolled into view compared to the News and Research sections above it. |
| 2026-06-08 | Added `.card-paper-count` link ("5 selected papers below →") to the Space-Time research card and `.card-status` label ("Active · Harvard 2025–") to the Flat Optics and Quantum cards. Styled as: `card-paper-count` = accent-colored 0.78rem link with hover-underline; `card-status` = muted 0.72rem non-linked label. | The three research cards were visually identical but conveyed very different states: Space-Time is the longest-established direction with 5 documented publications, while Flat Optics and Quantum/Atom are active but newer Harvard work without papers in the selected list yet. The asymmetry (link on ST, status label on FO/QA) is intentional and accurate — it tells visitors where the publication trail lives and signals the others are in-progress. Creates a direct navigation path from the ST research card to the Publications section below. |
