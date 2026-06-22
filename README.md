# RAFD static demo (GitHub Pages)

A pre-computed, fully static version of the RAFD demo: no server, no GPU. The
verdicts are the winning model's actual deterministic outputs, baked in by
`demo/build_static.py`.

## Files
- `index.html` - the page (self-contained CSS + JS)
- `data.js` - baked clip metadata + model verdicts (`window.RAFD_DATA`)
- `clips/` - the frames (16 per clip)

## Publish on GitHub Pages

**Option A - project page from a `/docs` folder (simplest):**
1. Copy this whole `site/` folder into your repo as `docs/` (or push the repo and
   point Pages at `code/demo/site`).
2. On GitHub: *Settings -> Pages -> Build and deployment -> Source: Deploy from a
   branch*, branch `main`, folder `/docs`. Save.
3. URL: `https://<user>.github.io/<repo>/`.

**Option B - dedicated repo:**
1. `git init` a repo whose root is this folder; push to `github.com/<user>/rafd-demo`.
2. *Settings -> Pages -> Source: branch `main`, folder `/ (root)`*.
3. URL: `https://<user>.github.io/rafd-demo/`.

Preview locally: `python -m http.server -d site 8000` then open
`http://localhost:8000` (open via http://, not file://, so `data.js` loads).

To refresh after changing the clip set: re-run
`.venv/bin/python demo/build_clips.py && .venv/bin/python demo/build_static.py`.
