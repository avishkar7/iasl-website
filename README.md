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
<li>A. Author, M. Levorato. <span class="t">“Paper Title.”</span> <span class="v">IEEE Venue, City, Month 2026</span>. <span class="links"><a href="https://doi.org/..." aria-label="DOI: Paper Title (2026)">DOI</a><a href="https://github.com/..." aria-label="Code: Paper Title (2026)">Code</a></span></li>
```

Every DOI / Code / arXiv link needs an `aria-label` naming the paper (in `research.html`, leave off the year), otherwise screen readers hear a list of identical "DOI" links. For a new year, copy a whole `<section class="section" id="y2023">…</section>` block, change the year in three places (`id`, the `<h2 class="label">` heading, list), and add a link to the year row (`<nav class="years">`) near the top. If the paper belongs to a research area, paste the same `<li>` into that area in `research.html`.

**Add news** — add a `<li>` at the top of the list in `updates.html`, and update the two `<div class="item">` blocks in the dark "Latest" band at the bottom of `index.html` (keep the newest two or three).

**Add a person** — in `group.html`, copy a `<div class="person">…</div>` into the right section. Keep the name as an `<h3 class="n">` heading and give every link an `aria-label` with the person's name:

```html
<div class="person"><h3 class="n">First Last</h3><div class="r">Ph.D. Student (CS)</div><div class="y">2026–present</div><div class="l"><a href="https://www.linkedin.com/in/..." aria-label="First Last on LinkedIn">LinkedIn</a></div></div>
```

Move people to "Ph.D. Alumni" when they graduate and add their current position as the second `<div class="r">` line.

**Header / footer** — they are repeated in every page. When you change the menu or footer, change it in all eight files (a find-and-replace across the folder works).

## Accessibility (WCAG 2.1 AA, required by UC policy IMT-1300)

The site passes an automated WCAG 2.1/2.2 AA check (axe) on every page. Keep it that way:

- **Colors** — use only the tokens in `css/style.css`; they are chosen to meet 4.5:1 contrast. Check any new color with the [WebAIM contrast checker](https://webaim.org/resources/contrastchecker/).
- **Headings** — one `<h1>` per page; section labels are `<h2 class="label">`; never skip a level.
- **Links** — link text must make sense on its own. Repeated text ("LinkedIn", "DOI") needs an `aria-label` that names the person or paper and starts with or contains the visible text.
- **Images** — every `<img>` needs `alt` text describing what the figure shows; put the explanation in the `<figcaption>`.
- **Header** — every page starts with the "Skip to main content" link and `<main id="main" tabindex="-1">`; the current page's nav link carries `aria-current="page"`.
- **Footer** — keep the "Report an accessibility barrier" link (UCI's reporting page); UC policy requires it.
- **Documents** — don't host PDFs or slides unless they are tagged/accessible; link to the publisher (DOI) instead.
- **Before publishing** — Tab through the changed page with the keyboard, and run [WAVE](https://wave.webaim.org/) on it.

## Open questions for the advisor

- [ ] **Undergraduate students** — confirm who should be listed under Undergraduates on `group.html` (current names come from the old live site and may be out of date).
- [ ] **Juliano Siloto Assine** — how to show his timeline (start year) on the Group page. His research keywords were removed for consistency with the other entries; only his LinkedIn is linked for now.
- [ ] **Malik Luti** ([LinkedIn](https://www.linkedin.com/in/malik-luti/)) — not on the Group page yet; ask how to list him (role, section, and years). He is a co-author on FUSCO (MILCOM 2025) and the semantic digital twin paper (SMARTCOMP Workshops 2026).

## Colors
Defined at the top of `css/style.css`: `--paper` (background), `--ink` (navy text), `--accent` (rust), `--accent-on-dark` (rust on the navy strip), `--band` (dark navy strip), `--focus` (keyboard focus ring).
