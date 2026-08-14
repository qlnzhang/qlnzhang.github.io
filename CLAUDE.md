# Project context for Claude Code

Personal portfolio site for a computer vision engineer. Hosted on GitHub Pages.

**This site is designed to last 20 years with near-zero maintenance.**
That constraint outranks every other consideration, including convenience,
modernity, and developer experience. Please read the constraints below before
proposing changes.

---

## Hard constraints — do not violate

**No build step.** No npm, no bundler, no package.json, no node_modules.
Files are edited and committed directly. `git push` is the entire deploy
pipeline.

**No external requests.** No CDNs, no Google Fonts, no analytics, no
third-party scripts. Every asset is served from this repo. The site must
render correctly with no network access beyond the page itself.

**No frameworks.** No React, Vue, Svelte, Tailwind, Bootstrap, or any static
site generator. Plain HTML and one CSS file. A framework chosen in 2026 will
be a migration burden by 2032.

**No JavaScript unless strictly necessary.** Currently the site uses zero JS
and should stay that way. Anything that requires JS to display content is a
failure mode in ten years.

**System fonts only.** The `--sans` and `--mono` stacks in `style.css` resolve
to fonts already present on the user's machine. Do not add webfonts.

**Durable media formats only.** JPEG and PNG for images. MP4/H.264 for video.
No WebP-only, no AVIF-only, no SVG animations. Video must include a `poster`
image so a still frame shows if playback fails.

---

## Structure

```
/index.html              tier 1 — the scan layer, 60-second read
/style.css               single source of truth for all styling
/work/_template.html     copy this to create a project page
/work/*.html             tier 2 — full technical writeups
/writing/_template.html  copy this to create a post
/writing/*.html          posts, named YYYY-MM-slug.html
/media/                  images and video, self-hosted
```

**Two-tier design.** `index.html` serves the recruiter or hiring manager who
spends 60 seconds and never scrolls deep. The `/work/` and `/writing/` pages
serve the engineer who will interview the author and wants real substance.
Do not merge these tiers or move depth onto the index.

---

## Style rules

All styling lives in `style.css`. Never inline styles into a page — a design
change must be possible by editing one file.

The corner brackets on `.frame` are the site's only decorative element. They
reference bounding-box overlay from object detection. Do not add further
ornament; the restraint is the point.

Colour, spacing, and type scale are defined as CSS custom properties at the
top of `style.css`. Change values there rather than adding new rules.

Dark mode is handled by `prefers-color-scheme`. Do not add a toggle — a
toggle needs JS and state persistence, both of which are maintenance burden.

---

## Content rules

**Every project card follows a six-part anatomy:**
1. Title — descriptive, no codenames
2. What it does — one plain sentence
3. The constraint — why the obvious approach fails *(the most important line)*
4. Result — a number, and what it cost
5. Visual evidence — image; video only when motion is the content
6. Metadata — year, stack, links

**Date-stamp everything.** Write "Data scientist at X, 2026–" not "Currently
a data scientist at X". Present-tense claims require the author to remember
to update them; dated claims age gracefully on their own.

**Never publish company material.** No client names, no internal metrics, no
work code, no proprietary data. Techniques are reproduced independently on
public datasets and those numbers are published instead. If a task would
involve pasting in code from the author's employer, stop and flag it.

**Placeholders in square brackets** — `[company]`, `[field]` — are unfilled.
Do not invent values for them.

---

## Things deliberately not built

Each of these was considered and rejected as a future maintenance burden:
analytics, contact form, comments, tag system, search, RSS, dark-mode toggle,
webfonts, CDN, build step, framework, CMS.

Do not add them, even if asked to "improve" or "modernise" the site. If a
feature genuinely seems necessary, say so and explain the maintenance cost
rather than implementing it silently.

---

## Adding content

**New project:** copy `work/_template.html` → rename → fill in → add a card
to the "Selected work" section of `index.html`.

**New post:** copy `writing/_template.html` → rename `YYYY-MM-slug.html` →
fill in → add a `.post` row to the "Writing" section of `index.html`.

**New media:** drop into `/media/`. Keep images under 400 KB, video under
3 MB. Total site media budget is roughly 8 MB.

Always update the "Last updated" line in the index footer.
