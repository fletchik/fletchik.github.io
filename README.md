# Personal homepage

One static page for GitHub Pages (user site). No framework, no build step.

| URL | File |
|---|---|
| `fletchik.github.io` | `index.html` |

The former conference page (`research.html`) and the business card (`card/`)
were removed on 17.11.2026; both are in git history if ever needed.

## CV

`resume.pdf` is the public variant built by
`~/master/job-search/google-search-user-trust-2026-11-13/build_cv_variants.py`
(variant `Public`: no employer name, no phone):

```bash
cp ~/master/output/pdf/Varvara_Nazarenko_CV_public.pdf ~/github_page/resume.pdf \
  && cp ~/github_page/resume.pdf ~/github_page/cv.pdf
```

`cv.pdf` is the same file under its old name, kept so links already handed out
keep working.

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
- `piefs-poster.pdf` — PIEFS poster, linked from the page

## Deploy

User site: served from the default branch, no Actions or Jekyll config needed.

```bash
git add -A && git commit -m "..." && git push
```

Live about a minute later at `https://fletchik.github.io`.
