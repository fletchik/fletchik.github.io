# Personal homepage

Two static pages for GitHub Pages (user site). No framework, no build step.

## Pages

| URL | File | Purpose |
|---|---|---|
| `fletchik.github.io` | `index.html` | **Hiring.** AI/ML Engineer positioning: experience, skills, CV. This is the URL to give recruiters. |
| `fletchik.github.io/research.html` | `research.html` | **Conferences.** The original academic page — bio, publications. Give this one at ICML / ICLR / poster sessions. |

Both share one design system: same CSS variables, same typography, same
left-meta-column row layout. They should always look like siblings.

Snapshot of the original academic page: `git show academic-v1:index.html`.

### Swapping them before a conference

If the academic page should temporarily sit at the root:

```bash
cp index.html hire.html && cp research.html index.html
# and swap back afterwards
```

Remember to fix `<link rel="canonical">` and `og:url` in whichever file moves.

## CV

`resume.pdf` is built from `~/cv/cv_public.tex`:

```bash
cd ~/cv && latexmk -pdf cv_public.tex \
  && cp cv_public.pdf ~/github_page/resume.pdf \
  && cp cv_public.pdf ~/github_page/cv.pdf
```

`cv.pdf` is the same file under its old name, kept so links already handed out
keep working. Drop it once you are sure none are in circulation.

**This repository is public. Two rules, no exceptions:**

1. **Never commit the named employer.** The pricing role is published as
   "Global commodities producer · name on request". The named variant stays
   out of this repo entirely — git history is public and cannot be un-published.
2. **No phone number in `cv.pdf`.** The file gets indexed by Google.

Check before every commit that touches the resume:

```bash
# EMPLOYER = the real company name, PHONE = the number. Never hardcode them here:
# this README is public too.
PAT="$EMPLOYER|diamond|$PHONE"
grep -riE "$PAT" . --exclude-dir=.git --exclude="*.pdf"
pdftotext resume.pdf - | grep -iE "$PAT"
```

Both must return nothing.

## Other files

- `profile.jpg` — 600×600 headshot
- `favicon.png`, `hse.png` — icons
- `piefs-poster.pdf` — PIEFS poster, linked from both pages
- `card/` — printable business card (`card-print.html` → `business-card.pdf`)

## Deploy

User site: served from the default branch, no Actions or Jekyll config needed.

```bash
git add -A && git commit -m "..." && git push
```

Live about a minute later at `https://fletchik.github.io`.
