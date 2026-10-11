# UCI IASL website

Plain HTML + one CSS file. No build step, no framework, no JavaScript.
Open any `.html` file in a browser to preview; push the folder to any static host (GitHub Pages, ICS web space) to publish.

```
index.html      Home: lab intro, research areas, latest news band
research.html   Research areas, each with its publications
group.html      People (faculty, students, alumni, visitors)
levorato.html   Faculty profile / CV
fund.html       Funded projects
papers.html     All publications by year
updates.html    Misc. Updates (news)
contact.html    Contact
img/research/    Research figures (compressed .webp)
css/style.css   All styling — colors and fonts are tokens at the top of the file
```

## Common edits

**Add a paper** — in `papers.html`, find the year's `<ol class="plain pubs">` and copy an existing `<li>`:

```html
<li>A. Author, M. Levorato. <span class="t">“Paper Title.”</span> <span class="v">IEEE Venue, City, Month 2026</span>. <span class="links"><a href="https://doi.org/...">DOI</a><a href="https://github.com/...">Code</a></span></li>
```

For a new year, copy a whole `<section class="section" id="y2023">…</section>` block, change the year in three places (`id`, label, list), and add a link to the year row (`<nav class="years">`) near the top. If the paper belongs to a research area, paste the same `<li>` into that area in `research.html`.

**Add news** — add a `<li>` at the top of the list in `updates.html`, and update the two `<div class="item">` blocks in the dark "Latest" band at the bottom of `index.html` (keep the newest two or three).

**Add a person** — in `group.html`, copy a `<div class="person">…</div>` into the right section. Move people to "Ph.D. Alumni" when they graduate and add their current position as the second `<div class="r">` line.

**Header / footer** — they are repeated in every page. When you change the menu or footer, change it in all eight files (a find-and-replace across the folder works).

## Open questions for the advisor

- [ ] **Undergraduate students** — confirm who should be listed under Undergraduates on `group.html` (current names come from the old live site and may be out of date).
- [ ] **Juliano Siloto Assine** — how to show his timeline (start year) on the Group page. His research keywords were removed for consistency with the other entries; only his LinkedIn is linked for now.
- [ ] **Research images** — the live research page shows a SeReMAS architecture figure (Dynamic Edge Computing) and a SmartDet image (Distributed Video Processing); neither is in the uci-iasl/website repo. Get the original files and add them to `img/research/`.
- [ ] **Malik Luti** ([LinkedIn](https://www.linkedin.com/in/malik-luti/)) — not on the Group page yet; ask how to list him (role, section, and years). He is a co-author on FUSCO (MILCOM 2025) and the semantic digital twin paper (SMARTCOMP Workshops 2026).

## Colors
Defined at the top of `css/style.css`: `--paper` (background), `--ink` (navy text), `--accent` (rust), `--band` (dark navy strip).
