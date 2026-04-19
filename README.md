# cpd-library

The knowledge base that ships inside the CPD Blackbook dashboard under
**My Tools → Library**. Hosted as static files on GitHub Pages; loaded
into the dashboard via iframe.

---

## Structure

```
cpd-library/
├── index.html                      ← the Library app itself
├── lifework-os-how-it-works.md     ← architecture doc (10 pages)
├── plans-onepager.pdf              ← all 7 tiers, commissions (1 page)
├── referral-playbook.pdf           ← 40% recurring playbook (8 pages)
├── rep-onboarding.docx             ← 30-day rep ramp (4 pages)
├── client-kickoff.docx             ← 5-day agency kickoff (6 pages)
├── fit-finder-scripts.txt          ← paste-and-go share copy
├── creator-launch.pdf              ← 7-day creator rollout (7 pages)
└── tool-cheatsheet.pdf             ← all 33 tools, one-liners (2 pages)
```

---

## Deploy

1. Push everything in this folder to the root of `cpd-library` (the
   repo named exactly that, lowercase).
2. Settings → Pages → Source: `Deploy from a branch` → `main` / `/ (root)`.
3. Wait ~60 seconds. Test at:
   **https://dexaintdead.github.io/cpd-library/**
4. In the dashboard, bump `CPD_VERSION` once to bust iframe cache.

---

## How the Library loads documents

The `DOCS` array inside `index.html` uses relative paths — so as long
as all files sit alongside `index.html` (as they do in this folder),
Open/Download/Print/Share all work automatically. No URL edits needed.

If you ever move docs to a different host (Supabase, Drive, CDN), swap
the `src:` values in the `DOCS` array for absolute URLs.

---

## Branding

All 5 PDFs and 2 .docx files share the same visual system:

- Black header bar with `CPD BLACKBOOK  │  LIFEWORK OS` wordmark left,
  doc title right in red
- Red-bar + gold-label callouts
- Consistent typography (Helvetica family for PDFs, Calibri for docx)
- Footer on every page: `cpdblackbook.com  •  The Library  •  page N  •  Apr 2026`

Updates to branding live in `_build_*.py` (for PDFs, uses `cpd_style.py`)
and inside the .docx builders directly. Not included in the repo — kept
in the working build directory.

---

## Updating content

Each doc has a build script — edit content, rerun the script, commit
the regenerated file. Build scripts live in the agency working dir,
not in this repo.

Version stamps: every doc footer shows the month/year. When you ship
a new version, update the `updated:` field in the DOCS array inside
`index.html` too.
