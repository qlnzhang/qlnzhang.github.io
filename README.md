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

**Stills on `index.html`, video only on `/work/` and `/writing/` pages.** The
index is a 60-second scan; a loop on every card competes with the constraint
line, which is the sentence doing the most hiring work. The reader who wants
to see it move will click through.

Video only when motion is the actual content — tracking, occlusion recovery,
temporal jitter. If a single frame conveys it, motion is decoration and a
still is better in every way.

MP4/H.264, muted, looping, with a `poster` fallback image. Never embed
YouTube. **Never GIF** — roughly 15-20x the file size for worse quality, and
a 256-colour palette bands visibly on road imagery.

```
ffmpeg -i in.mov -t 8 -an -vf "scale=800:-2" -c:v libx264 -crf 26 \
       -movflags +faststart out.mp4
```

## Before you publish anything

- No client names, no company data, no internal metrics, no work code
- Techniques rebuilt independently on public datasets (BDD100K, Cityscapes, KITTI)
- Written on your own machine, on your own time
- Ask your manager once, in writing, and keep the reply

## Rhythm

One note a month. Roughly two hours, one Sunday afternoon:

1. Open the brag doc, pick the most interesting thing solved this month
2. `cp writing/_template.html writing/YYYY-MM-slug.html`
3. Write 400-800 words: symptom → investigation → root cause → fix →
   result → what I'd do differently
4. Add one figure or table — a note with no evidence is an opinion piece
5. Add a `.post` row at the top of the Writing section in `index.html`
6. Update the footer date, commit, push

Keep them short. The failure mode is deciding each note must be an essay,
missing month four, and never restarting. Twelve short notes beat three
polished ones and nine months of silence.

Missed a month? Skip it and carry on. Never backdate — a visible gap costs
nothing, a fabricated timeline costs everything.

Source material comes from the brag doc, not from brainstorming topics.
Trying to invent topics produces tutorial content. Reviewing what you
actually solved produces the good stuff.

## Design constraints

See `CLAUDE.md`. Short version: no build step, no dependencies, no frameworks,
no external requests, system fonts only. The site should still render in 2046.
