# Website improvement plan (nightly runs, Nov 11–17, 2026; 12am, 3am, 6am Eastern)

Work branch: `claude/site-improvements` → one pull request into `main`.
The live site (yessenov.org) publishes from `main`; nothing goes live until the owner merges.

Each run: take the **first unchecked task** below, finish it, verify it, tick it here
(`- [x]`, with the date and a one-line note), commit, push, and update the PR.
If a task is too big for one run, split it: tick what is done and add a sub-task
right below it for the next run.

## Task queue

### Night 1 — Wed Nov 11
- [x] **T1 Housekeeping.** *(done 2026-11-10: Profile.pdf deleted, footer updated, PR opened)* Delete `Profile.pdf`. Replace the footer text "© 2026 · Harvard University" with "© 2026 Murat Yessenov · Last updated November 2026". Open the PR.
- [x] **T2 Newest papers → News + metrics.** *(partly done 2026-11-11: metrics updated, 8 News items added; months/DOIs pending, see T2b)* Add News items (month + year, newest first) for the recent published items listed under *Recent items* below. Update the metrics in About and Publications to the current numbers (Google Scholar: 2,620 citations, h-index 25 as of Nov 9, 2026; ~54 peer-reviewed journal articles). Use "50+ peer-reviewed articles · 2,600+ citations". Keep News to the 6–8 most recent items.
- [x] **T2b Exact months and links for News.** *(done 2026-11-11, 3am run: months and DOIs found via web search of public publisher/arXiv/Harvard records, since Crossref and doi.org stayed blocked; Optica date corrected to Jan 2026; APL Photonics month/DOI and patent link still open, moved to T6)* Crossref, doi.org and publisher sites were unreachable from the session on 2026-11-11, so the 2026/2025 paper items show the year only and have no "Read →" link. Get the publication months from Crossref, re-sort News newest first, add DOI links (and the patent link), and check the "Jun 2026" date on the Optica item: the CV puts that paper in Optica 13(2), which suggests an earlier 2026 issue.
- [x] **T3 Selected Publications refresh.** *(done 2026-11-11, 6am run: 8 entries; laser-array paper has no arXiv link and an abbreviated author list, see T6)* Add *Ultrafast space-time optical merons* (Nat. Commun. 2025, first author) and *On-chip space–time wave packet laser array* (Nat. Photon. 2026). Keep 6–8 entries total, each with venue, year, authors (own name bold), one-line teaser, Paper + arXiv links.

### Night 2 — Thu Nov 12
- [ ] **T4 Full publications page, part 1.** Create `publications.html` in the site's style (same header/nav/footer, `assets/css/style.css`). Journal articles grouped by year, newest first; own name bold; each with DOI link and arXiv link when one exists. This run: preprints + 2024–2026.
- [ ] **T5 Full publications page, part 2.** Add 2018–2023 and a Patents section. Add "Publications" to the nav on every page pointing to `/publications.html`, and change the homepage "Full list on Google Scholar" link to point to the new page (keep Scholar as a secondary link).
- [ ] **T6 Verify the publication list.** Check every entry against Crossref/the publisher (title, authors, journal, volume, pages/article number, year, DOI). The source list below comes from the CV and has known errors (see *Known CV errors*). Fix them on the page.
  Also (carried over from T2b): find the month and DOI of the APL Photonics 130 m paper (News currently shows "2026" with an arXiv:2607.12311 link) and the issue date and a public link for U.S. Patent 12,613,365 (none found by web search on 2026-11-11); update the News items. Re-check the News DOIs against Crossref: 10.1038/s41566-026-02003-0 (Sep 2026), 10.1364/OL.605394 (Jul 2026), 10.1364/OPTICA.582198 (Jan 2026), 10.1038/s41467-025-63641-6 (Sep 2025).
  Also (from T3): confirm the full author order of the Nat. Photon. laser-array paper (web sources disagree on where B. Huh falls; the homepage shows "J. Lee, H. Ren, Y. G. Liu, M. Yessenov, Y. Wei, B. Huh, …, M. Khajavikhan" as in the CV) and whether it has an arXiv version.

### Night 3 — Fri Nov 13
- [ ] **T7 Figures.** For each of the four research topics, pick one representative figure from one of that topic's papers (see *Figure rules*). Save to `assets/img/research/<slug>.jpg` (or .webp), ~1200 px wide, ≤ 250 KB. Record source paper, figure number and license in the *Figure log* below.
- [ ] **T8 Research page template + Topic 1 (Space-time wave packets).** Create `research/space-time-wave-packets.html`.
- [ ] **T9 Topic 2 (Non-separable partially coherent light).** Create `research/partially-coherent-light.html`.

### Night 4 — Sat Nov 14
- [ ] **T10 Topic 3 (Self-imaging and 3D light shaping).** Create `research/self-imaging.html`.
- [ ] **T11 Topic 4 (Compact instrumentation with r-CBGs).** Create `research/compact-instrumentation.html`.
- [ ] **T12 Homepage research section.** Replace the three research cards with four figure cards (one per topic: figure thumbnail, title, 1–2 sentence summary); clicking a card opens its topic page. Update the section intro, bio tags and the JSON-LD `knowsAbout` to match the four topics.

### Night 5 — Sun Nov 15
- [ ] **T13 QA.** Every internal and external link resolves (DOIs, arXiv, images, nav anchors from subpages). No console errors. Layout works at 375 px wide with no horizontal scroll. Fix what fails.
- [ ] **T14 Content audit.** Consistent numbers and wording across pages; each page has its own `<title>`, description, canonical URL and og tags; alt text on every figure; one `<h1>` per page.
- [ ] **T15 Polish.** `sitemap.xml`, `robots.txt`, a simple `404.html` in the site style; `loading="lazy"` and width/height on below-the-fold images.

### Nights 6–7 — Mon Nov 16, Tue Nov 17 (buffer)
- [ ] **T16 Finish anything unchecked above, then address the owner's PR comments, then small polish.** If nothing is left, make no changes.

## Site rules
- Plain static HTML + the existing `assets/css/style.css` and `assets/js/main.js`. No build step, no frameworks, no new fonts. Follow `.interface-design/system.md` (navy/steel palette, Lora headings, Inter body, no dark mode).
- Use root-relative links (`/`, `/publications.html`, `/research/self-imaging.html`, `/#contact`) so subpages work.
- Never touch `CNAME`. Never push to `main`. Never merge the PR.
- No CV PDF or CV download link on the site (the owner removed it on Nov 10, 2026). The on-page CV section stays.
- Only published, public information. When unsure whether something is public, leave it out and mention it in the PR.

## Research topics (owner's grouping)

A paper may appear under more than one topic. Each topic page: title, 2–3 paragraph plain-language overview of the published results, the figure with caption and credit, a short "Key results" list, and the topic's publication list (same format as `publications.html`), plus a link back to `/#research`.

1. **Space-time wave packets** (`space-time-wave-packets`): the two PRLs (Accelerating and decelerating STWPs, PRL 125, 233901, 2020; Veiled Talbot effect, PRL 125, 243901, 2020); Anomalous refraction, Nat. Photon. 14, 416 (2020); the Nature Communications papers (free-space delay line 2020; hybrid guided space-time modes 2020; localized in all dimensions 2022; STWPs in multimode fibers 2025; space-time optical merons 2025; space-time surface plasmon polaritons 2025); On-chip STWP laser array, Nat. Photon. 2026; the review (Adv. Opt. Photon. 14, 455, 2022) and the tutorial (JOSA A 42, 1295, 2025).
2. **Non-separable partially coherent light** (`partially-coherent-light`): Non-diffracting broadband incoherent space-time fields, Optica 6, 598 (2019), and the Optics Letters paper(s) on incoherent light — most likely *Changing the speed of optical coherence in free space*, Opt. Lett. 44, 5125 (2019). Read the abstracts to confirm; other candidates (e.g., *The propagation speed of optical speckle*, Sci. Rep. 2023) go in only if they clearly fit — list any additions in the PR for the owner to confirm.
3. **Self-imaging and 3D light shaping** (`self-imaging`): Veiled Talbot effect (PRL 2020); The space-time Talbot effect (APL Photonics 6, 056105, 2021); Observation of the spatially structured Montgomery effect in free space (Optica 13, 195, 2026); Self-healing of the Montgomery pattern (Opt. Lett. 51, 4008, 2026); Chebyshev self-imaging from inverse-sampled angular spectra (arXiv:2608.22415, 2026 preprint). This is the current Harvard work.
4. **Compact instrumentation with rotated chirped volume Bragg gratings (r-CBGs)** (`compact-instrumentation`): the three Optics Letters papers — Ultra-compact synthesis of space-time wave packets (Opt. Lett. 48, 2500, 2023; DOI 10.1364/OL.483902), Rotated chirped volume Bragg gratings for compact spectral analysis (Opt. Lett. 48, 1180, 2023), Compact dual-band spectral analysis via multiplexed r-CBGs (Opt. Lett. 48, 5137, 2023); the patents (U.S. Patent 12,613,365 granted 2026; U.S. applications 18/532,698 and 18/532,983 — verify titles/status on Google Patents; the owner called these "the 2 patents", so flag the count in the PR); and Tau Optics Inc., a CREOL spin-out the owner co-founded to commercialize r-CBG spectrometers, supported by an NSF STTR Phase I award (verify on the public NSF award search; state the amount only if it appears there).

## Recent items (for News, T2)
- Nat. Photon. 2026 — On-chip space–time wave packet laser array (Lee, …, Yessenov, …, Khajavikhan)
- Opt. Lett. 51, 4008 (2026) — Self-healing of the Montgomery pattern (first author: Harvard undergraduate mentee Athena Xu)
- APL Photonics 11, 106108 (2026) — Selective avoidance of multiple line-of-sight obstacles at 130 m using locally bending space-time wave packets
- U.S. Patent 12,613,365 granted (2026)
- Invited talk, IEEE Photonics Society Summer Topical Meeting, Tulum, Mexico (Jul 2026)
- Invited talk, EIPBN 2026, Denver, CO (May 2026)
- Nat. Commun. 16, 8592 (2025) — Ultrafast space-time optical merons in momentum-energy space
- Nat. Commun. 16, 10697 (2025) — Observation of space-time surface plasmon polaritons
- JOSA A 42, 1295 (2025) — Optical spatiotemporal Fourier synthesis: tutorial
Get exact months from Crossref publication dates.

## Figure rules
- The owner is an author of every paper here. Prefer figures from open-access (CC BY) versions — Nature Communications, Optica, APL Photonics — or the authors' own arXiv versions (arXiv e-print source archives contain the original figure files).
- Every figure gets a caption ending with a credit line, e.g. "Figure adapted from M. Yessenov et al., Optica 13, 195 (2026), CC BY 4.0." For non-open-access journals, use the arXiv version's figure and cite the published paper.

## Figure log
| Topic | Paper | Figure | License / source | File |
|---|---|---|---|---|

## Known CV errors (fix on the site)
- *Ultra-compact synthesis of space-time wave packets* is Opt. Lett. 48, 2500 (**2023**), not 2022.
- *Space-time wave packets localized in all dimensions* is Nat. Commun. 13 (**2022**), not 2021.
- *Refraction of space-time wave packets in a dispersive medium* and *Arbitrarily accelerating space-time wave packets* both carry "Opt. Lett. 47(7), 1630–1633" in the CV; at least one is wrong.
- "Abouraddy, T. B. A. F." in the 2025 Opt. Lett. 50, 4698 entry is garbled; the author is A. F. Abouraddy.
- Truncated author lists ("...") must be completed from Crossref on the full publications page.

## Source publication list (from the CV, Nov 2026 — verify every entry)
- Hall, L. A., & Yessenov, M. (2026). Chebyshev self-imaging from inverse-sampled angular spectra. arXiv preprint arXiv:2608.22415.
- Hall, L. A., Yessenov, M., Lebron, I., & Abouraddy, A. F. (2026). Selective avoidance of multiple line-of-sight obstacles at 130 m using locally bending space-time wave packets. APL Photonics, 11 (10): 106108
- Lee, J., Ren, H., Liu, Y. G., Yessenov, M., Wei, Y., Huh, B., ... & Khajavikhan, M. (2026). On-chip space–time wave packet laser array. Nature Photonics, 1-8.
- Xu, A., de Vries, O., Palmieri, A., Yessenov, M., Abouraddy, A. F., & Capasso, F. (2026). Self-healing of the Montgomery pattern. Opt. Lett., 51(14), 4008-4011. 
- Yessenov, M., Sacchi, L., Palmieri, A., Hall, L. A., Abouraddy, A. F., & Capasso, F. (2026). Observation of the spatially structured Montgomery effect in free space. Optica, 13(2), 195-202.
- Hall, L. A., Yessenov, M., Schepler, K. L., & Abouraddy, A. F. (2025). Universality and non-differentiability: A new perspective on angular dispersion in optics. APL Photonics, 10(12).
- Ichiji, N., Kikuchi, H., Yessenov, M., Schepler, K. L., Abouraddy, A. F., & Kubo, A. (2025). Observation of space-time surface plasmon polaritons. Nature Communications, 16(1), 10697.
- Yaraghi, S., Mhibik, O., Yessenov, M., Miller, J. K., Parto, M., Johnson, E. G., ... & Divliansky, I. (2025). Resonance-free Fabry-Pérot cavity via unrestricted orbital-angular-momentum ladder-up. Nature Communications, 16(1), 10362.
- Yessenov, M., Dorrah, A. H., Guo, C., Hall, L. A., Park, J. S., Free, J., ... & Abouraddy, A. F. (2025). Ultrafast space-time optical merons in momentum-energy space. Nature Communications, 16(1), 8592.
- Yessenov, M., & Abouraddy, A. F. (2025). Optical spatiotemporal Fourier synthesis: tutorial. Journal of the Optical Society of America A, 42(9), 1295-1315.
- Hall, L. A., Yessenov, M., Romer, M. A., & Abouraddy, T. B. A. F. (2025). Long-distance axial spectral encoding using space-time wave packets. Optics Letters, 50(15), 4698-4701.
- Abouraddy, A. F., Yessenov, M., Divliansky, I., & Watnik, A. T. (2025). New frontiers in spatiotemporally structured light. Optics and Photonics News, 36(7), 38-45.
- Su, X., Zou, K., Wang, Y., Yessenov, M., Zhou, H., Song, H., ... & Willner, A. E. (2025). Space-time wave packets in multimode optical fibers with controlled dynamic motions and tunable group velocities. Nature Communications, 16(1), 2027.
- Ichiji, N., Yessenov, M., Schepler, K. L., Abouraddy, A. F., & Kubo, A. (2024). Exciting space-time surface plasmon polaritons by irradiating a nanoslit structure. JOSA A, 41(3), 396-405.
- Yessenov, M., Romer, M., Ichiji, N., & Abouraddy, A. F. (2024). Experimental realization of Lorentz boosts of space-time wave packets. Phys. Rev. A, 109(1), 013509.
- Mhibik, O., Yessenov, M., Glebov, L., Abouraddy, A. F., & Divliansky, I. (2023). Compact dual-band spectral analysis via multiplexed rotated chirped volume Bragg gratings. Opt. Lett., 48(19), 5137-5140.
- Wan, Z., Yessenov, M., & Padgett, M. J. (2023). The propagation speed of optical speckle. Scientific Reports, 13(1), 9071.
- Yessenov, M., & Abouraddy, A. F. (2023). Relativistic transformations of quasi-monochromatic paraxial optical beams. Phys. Rev. A, 107(4), 042221.
- Yessenov, M., Mhibik, O., Mach, L., Hayward, T. M., Menon, R., Glebov, L., ... & Abouraddy, A. F. (2022). Ultra-compact synthesis of space-time wave packets. Opt. Lett., 48(10), 2500-2503.
- Mhibik, O., Yessenov, M., Mach, L., Glebov, L., Abouraddy, A. F., & Divliansky, I. (2023). Rotated chirped volume Bragg gratings for compact spectral analysis. Opt. Lett., 48(5), 1180-1183.
- Ichiji, N., Kikuchi, H., Yessenov, M., Schepler, K. L., Abouraddy, A. F., & Kubo, A. (2023). Observation of ultrabroadband striped space-time surface plasmon polaritons. ACS Photon., 10(2), 374-382.
- Shen, Y., Zhan, Q., Wright, L. G., Christodoulides, D. N., Wise, F. W., Willner, A. E., ... & Forbes, A. (2023). Roadmap on spatiotemporal light fields. J. of Opt., 25(9), 093001.
- Minoofar, A., Zou, K., Pang, K., Song, H., Karpov, M., Yessenov, M., ... & Willner, A. E. (2022). Generation of OAM-carrying space-time wave packets with time-dependent beam radii using a coherent combination of multiple LG modes on multiple frequencies. Optics Express, 30(25), 45267-45278.
- Zou, K., Su, X., Yessenov, M., Pang, K., Karapetyan, N., Karpov, M., ... & Willner, A. E. (2022). Tunability of space-time wave packet carrying tunable and dynamically changing OAM value. Opt. Lett., 47(21), 5751-5754.
- Pang, K., Zou, K., Zhao, Z., Song, H., Zhou, Y., Karpov, M., Yessenov, M. ... & Willner, A. E. (2022). Experimental demonstration of dynamic spatiotemporal structured beams that simultaneously exhibit two orbital angular momenta by combining multiple frequency lines, each carrying multiple Laguerre–Gaussian modes. Opt. Lett, 47(16), 4044-4047.
- Yessenov, M., Chen, Z., Lavery, M. P., & Abouraddy, A. F. (2022). Vector space-time wave packets. Opt. Lett. 47, 4131-4134
- Pang, K., Zou, K., Song, H., Karpov, M., Yessenov, M., Zhao, Z., ... & Willner, A. E. (2022). Synthesis of near-diffraction-free orbital-angular-momentum space-time wave packets having a controllable group velocity using a frequency comb. Opt. Express, 30(10), 16712-16724.
- Yessenov, M., Hall, L. A., Schepler, K. L., & Abouraddy, A. F. (2022). Space-time wave packets. Adv. Opt. Photon. 14(3), 455-570.
- Yessenov, M., Faryadras, S., Benis, S., Hagan, D. J., Van Stryland, E. W., & Abouraddy, A. F. (2021). Refraction of space-time wave packets in a dispersive medium. Opt. Lett. 47 (7), 1630-1633.
- Yessenov, M., Free, J., Chen, Z., Johnson, E. G., Lavery, M. P., Alonso, M. A., & Abouraddy, A. F. (2021). Space-time wave packets localized in all dimensions. Nat. Commun. 13 (1), 1-13
- Diouf, M., Harling, M., Yessenov, M., Hall, L. A., Abouraddy, A. F., & Toussaint, K. C. (2021). Space-time vector light sheets. Opt. Exp., 29(23), 37225-37233.
- Hall, L. A., Yessenov, M., and Abouraddy, A. F. (2021). Arbitrarily accelerating space-time wave packets, Opt. Lett., 47 (7), 1630-1633.
- Yessenov, M., Bhaduri, B., & Abouraddy, A. F. (2021). Refraction of space-time wave packets: I. Theoretical principles. J. Opt. Soc. Am. A 38(10) 1409-1422.
- Allende Motz A. A., Yessenov, M., Bhaduri, B., and Abouraddy, A. F. (2021). Refraction of space-time wave packets: II. Experiments at normal incidence. J. Opt. Soc. Am. A 38(10) 1450-1461 
- Yessenov, M., Allende Motz A. A., Bhaduri, B., and Abouraddy, A. F. (2021). Refraction of space-time wave packets: III. Experiments at oblique incidence. J. Opt. Soc. Am. A 38(10) 1462-1470 
- Hall, L. A., Yessenov, M., Ponomarenko, S. A., & Abouraddy, A. F. (2021). The space-time Talbot effect. APL Photonics 6 (5), 056105. 
- Yessenov, M., Hall, L. A., & Abouraddy, A. F. (2021). Engineering the optical vacuum: Arbitrary magnitude, sign, and order of dispersion in free space using space-time wave packets. ACS Photon., 8, 8, 2274–2284
- Allende Motz A. A., Yessenov, M., and Abouraddy, A. F. (2021). Isochronous space-time wave packets, Opt. Lett. 46 (10), 2260-2263.
- Hall, L. A., Yessenov, M., and Abouraddy, A. F. (2021). Space–time wave packets violate the universal relationship between angular dispersion and pulse-front tilt, Opt. Lett. 46, 1672-1675.
- Allende Motz A. A., Yessenov, M., and Abouraddy, A. F. (2021). Axial spectral encoding of space-time wave packets. Physical Review Applied, 15(2), 024067.
- Yessenov, M., Hall, L. A., Ponomarenko, S. A., & Abouraddy, A. F. (2020). Veiled talbot effect. Physical Review Letters, 125(24), 243901.
- Yessenov, M., & Abouraddy, A. (2020). Accelerating and decelerating space-time optical wave packets in free space, Physical Review Letters., 125, 233901.
- Yessenov, M., Bhaduri, B., Delfyett, P. J., & Abouraddy, A. F. (2020). Free-space optical delay line using space-time wave packets. Nature Communications, 11(1), 1-10.
- Shiri, A., Yessenov, M., Webster, S. et al. Hybrid guided space-time optical modes in unpatterned films. Nature Communications 11, 6273 (2020).
- Bhaduri, B., Yessenov, M., & Abouraddy, A. F. (2020). Anomalous refraction of optical spacetime wave packets. Nature Photonics, 14, 416–421 (2020)
- Shiri, A., Yessenov, M., Aravindakshan, R., & Abouraddy, A. F. (2020). Omni-resonant space–time wave packets. Optics Letters, 45(7), 1774-1777.
- Yessenov, M., Ru, Q., Schepler, K. L., Meem, M., Menon, R., Vodopyanov, K. L., & Abouraddy, A. F. (2020). Mid-infrared diffraction-free space-time wave packets. OSA Continuum, 3(3), 420-429.
- Schepler, K., Yessenov, M., Zhiyenbayev, Y., & Abouraddy, A. F. (2020). Space--Time Surface Plasmon Polaritons: A New Propagation-Invariant Surface Wave Packet. ACS Photonics.
- Yessenov, M., & Abouraddy, A. F. (2019). Changing the speed of optical coherence in free space. Optics letters, 44(21), 5125-5128. 
- Yessenov, M., Bhaduri, B., Kondakci, H. E., Meem, M., Menon, R., & Abouraddy, A. F. (2019). Non-diffracting broadband incoherent space–time fields. Optica, 6(5), 598-607. 
- Yessenov, M., Bhaduri, B., Kondakci, H. E., & Abouraddy, A. F. (2019). Weaving the rainbow: Space-time optical wave packets. Optics and Photonics News, 30(5), 34-41. 
- Yessenov, M., Mach, L., Bhaduri, B., Mardani, D., Kondakci, H. E., Atia, G. K., ... & Abouraddy, A. F. (2019). What is the maximum differential group delay achievable by a space-time wave packet in free space? Optics express, 27(9), 12443-12457. 
- Bhaduri, B., Yessenov, M., Reyes, D., Pena, J., Meem, M., Fairchild, S. R., ... & Abouraddy, A. F. (2019). Broadband space-time wave packets propagating 70 m. Optics letters, 44(8), 2073-2076.
- Yessenov, M., Bhaduri, B., Kondakci, H. E., & Abouraddy, A. F. (2019). Classification of propagation-invariant space-time wave packets in free space: Theory and experiments. Physical Review A, 99(2), 023856. 
- Bhaduri, B., Yessenov, M., & Abouraddy, A. F. (2019). Space–time wave packets that travel in optical materials at the speed of light in vacuum. Optica, 6(2), 139-146.
- Bhaduri, B., Yessenov, M., & Abouraddy, A. F. (2018). Meters-long propagation of diffraction-free space-time light-sheets. Optics express, 26(16), 20111-20121.
- Kondakci, H. E., Yessenov, M., Meem, M., Reyes, D., Thul, D., Fairchild, S. R., ... & Abouraddy, A. F. (2018). Synthesizing broadband propagation-invariant space-time wave packets using transmissive phase plates. Optics Express, 26(10), 13628-13638.

### Patents (from the CV)
- Divliansky, I., Abouraddy, A., Glebov, L., Mhibik, O., & Yessenov, M. (2026). U.S. Patent No. 12,613,365.
- Divliansky, I., Abouraddy, A., Glebov, L., Mhibik, O., & Yessenov, M. (2024). Spectrometer with rotated volume Bragg grating. U.S. Patent Application 18/532,698.
- Divliansky, I., Abouraddy, A., Glebov, L., Mhibik, O., & Yessenov, M. (2024). Systems and methods using a pair of rotated volume Bragg gratings for laser amplification. U.S. Patent Application 18/532,983.

## Run log
- 2026-11-10 09:58 ET — T1 Housekeeping — done. Deleted `Profile.pdf` (no page linked to it); footer now "© 2026 Murat Yessenov · Last updated November 2026"; opened PR. No PR existed before this run, so no owner feedback to act on. Verified: index.html 200, all local assets present, HTML balanced, no horizontal scroll at 375 px.
- 2026-11-11 00:06 ET — T2 News + metrics — partly done. No PR comments from the owner. About and Publications metrics now "50+ peer-reviewed articles · 2,600+ citations". News now 8 items (2026 Nat. Photon. laser array, APL Photonics 130 m, OL Montgomery self-healing, U.S. Patent 12,613,365, Jul 2026 Tulum talk, Jun 2026 Optica, May 2026 EIPBN talk, 2025 Nat. Commun. merons); older items dropped from News. Crossref, doi.org, nature.com, optica.org and arXiv were blocked by the session network policy, so months and DOI links were not added; added T2b. Verified: index.html 200, all local assets present, HTML balanced, no horizontal scroll at 375 px, no console errors.
- 2026-11-11 03:10 ET — T2b News months and links — done (two items left for T6). No PR comments from the owner. Crossref, doi.org, arXiv and nature.com blocked again; WebSearch worked, and months/DOIs were taken from public records it returned (nature.com article URL, Harvard SEAS/Capasso-group news posts, Nature Index, RePEc). News re-sorted: 2026 APL Photonics (arXiv link), 2026 patent, Sep 2026 Nat. Photon. (DOI), Jul 2026 Opt. Lett. (DOI), Jul 2026 Tulum, May 2026 EIPBN, Jan 2026 Optica (was Jun; Optica 13(2) is the January issue), Sep 2025 Nat. Commun. merons (DOI). Verified: index.html 200, local assets present, HTML balanced, no horizontal scroll at 375 px, no console errors; external links could not be curled from the session (proxy 403).
- 2026-11-11 06:14 ET — T3 Selected Publications — done. No PR comments from the owner. Added *On-chip space–time wave packet laser array* (Nat. Photon. 2026, Paper link only; no arXiv version found) and *Ultrafast space-time optical merons* (Nat. Commun. 2025, arXiv:2503.11980); list now 8 entries, featured Optica paper first, then newest first. Full author lists for the Optica 2026 and Opt. Lett. 2023 entries (the latter previously showed only two authors); Optica title now the published one ("Observation of the spatially…"); teasers rewritten in plain physical terms from the abstracts, hype removed; research-card link text no longer says "5 selected papers". Sources: arXiv listings, Nature Index, TU/e research portal and library records via web search (Crossref, arXiv, nature.com still blocked). Verified: index.html 200, local assets present, HTML balanced, no horizontal scroll at 375 px, no console errors.
