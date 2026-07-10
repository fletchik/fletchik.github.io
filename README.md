# Personal homepage

Single static page for GitHub Pages (user site). No framework, no build step.

## Files
- `index.html` — the page.
- `profile.jpg` — 600×600 headshot.
- `cv.pdf` — optional; add it if you want the CV link to work.

## Before publishing
Fill in the `EDIT:` placeholders in `index.html`:
- the `mailto:` email (appears twice: in the bio and in the links row)
- `github`, `scholar`, `linkedin` links
- add `cv.pdf` next to `index.html` (or delete the `cv` link)

## Deploy to GitHub Pages (user site)

A **user site** is served at `https://<username>.github.io` and deploys
automatically from the default branch — no Actions, no Jekyll config needed.

1. Create a repo named **exactly** `<username>.github.io` on GitHub (public).
2. From this folder:
   ```bash
   git remote add origin git@github.com:<username>/<username>.github.io.git
   git branch -M main
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a
   branch → Branch: `main` / `root`**. (For user sites this is usually on by default.)
4. Wait ~1 minute, then open `https://<username>.github.io`.

To update later: edit files, then `git add -A && git commit -m "..." && git push`.
