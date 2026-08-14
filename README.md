# Personal site

Plain HTML. No build step. Edit a file, commit, push — that's the deploy.

## Deploying (first time)

1. Create a repo named exactly `<your-username>.github.io`
2. Put these files in the root, commit, push
3. Settings → Pages → Source: `main` branch, `/` root
4. Live at `https://<your-username>.github.io` in about a minute

**Custom domain later:** buy a domain (~$15/yr), add a file named `CNAME`
containing just the domain, point DNS at GitHub Pages. The domain outlasts
any hosting platform — worth doing before you put the URL on a CV.

## Local preview

```
cd site
python -m http.server 8000
```

Then open `http://localhost:8000`. The `python -m http.server` step matters —
opening `index.html` directly via `file://` breaks the absolute paths like
`/style.css`.

## Adding a project

1. `cp work/_template.html work/your-project.html`
2. Fill in the bracketed placeholders
3. Add a card to the "Selected work" section in `index.html`
4. Update the "Last updated" line in the footer

## Adding a post

1. `cp writing/_template.html writing/2026-09-your-slug.html`
2. Fill in
3. Add a `.post` row to the "Writing" section in `index.html`
4. Update the footer date

## Media

Goes in `/media/`. Images under 400 KB, video under 3 MB, total budget ~8 MB.

Video only when motion is the actual content — tracking, temporal smoothing,
frame-to-frame behaviour. Otherwise a still image is better in every way.
MP4/H.264, muted, looping, with a `poster` fallback image. Never embed YouTube.

## Before you publish anything

- No client names, no company data, no internal metrics, no work code
- Techniques rebuilt independently on public datasets (BDD100K, Cityscapes, KITTI)
- Written on your own machine, on your own time
- Ask your manager once, in writing, and keep the reply

## Rhythm

Roughly four hours a month, one Sunday afternoon:

- Months 1, 4, 7, 10 — deep post (1500-2500 words)
- Months 2, 5, 8, 11 — short note (400-800 words)
- Months 3, 6, 9, 12 — no post; polish a repo, ship a tool update

Source material comes from the brag doc, not from brainstorming topics.
Trying to invent topics produces tutorial content. Reviewing what you
actually solved produces the good stuff.

## Design constraints

See `CLAUDE.md`. Short version: no build step, no dependencies, no frameworks,
no external requests, system fonts only. The site should still render in 2046.
