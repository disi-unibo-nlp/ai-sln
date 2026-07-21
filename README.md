# AI-SLN — project website

Static site (single `index.html` + `assets/`). No build step.

## Publish on GitHub Pages

**Option A — user/organization site (`<username>.github.io`)**
1. Create a repo named exactly `<username>.github.io`.
2. Copy the **contents** of this folder (`index.html`, `assets/`, `.nojekyll`) to the repo **root**.
3. Push to the `main` branch. The site goes live at `https://<username>.github.io/`.

**Option B — project site (any repo)**
1. Put these files at the repo root (or in a `/docs` folder).
2. Repo → **Settings → Pages** → *Build and deployment* → **Deploy from a branch** → branch `main`, folder `/ (root)` (or `/docs`).
3. Live at `https://<username>.github.io/<repo>/`.

## Notes
- `.nojekyll` tells GitHub Pages to serve the files as-is (no Jekyll processing).
- All links are relative, so it works at both a root domain and a `/repo/` sub-path.
- Fonts load from Google Fonts (with system fallbacks); everything else is local.
- The demo imagery is de-identified and served downscaled / as sprites on purpose.
