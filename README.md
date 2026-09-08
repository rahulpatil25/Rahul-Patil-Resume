# Rahul Patil — Resume

A single-file resume site that doubles as the source for the PDF recruiters get.

- **`index.html`** — the whole resume: content, styles and a print stylesheet. No build step.
- **`Rahul-Patil-Resume.pdf`** — generated from `index.html`; linked by the *Download PDF* button.
- **`assets/`** — headshot plus self-hosted Inter / Source Serif 4 subsets, so the page renders
  identically offline and in the PDF.

## Editing

Everything lives in `index.html`. Content is plain HTML in reading order — header, summary,
metrics, experience, skills, education — which is also the order an ATS parser sees.

The `@media print` block at the bottom of the `<style>` is what keeps the PDF to **one page**:
the photo, the download button and the per-role stack line drop out, the metric tiles collapse to
a single line, and the skill chips become inline text. If you add a bullet, check the page count
before committing.

## Regenerating the PDF

From a browser: **Print → Save as PDF**, paper A4, margins *Default*, headers and footers *off*
(the page sets its own `@page` margins).

Or headless, from the repo root:

```sh
chrome --headless --no-pdf-header-footer \
  --print-to-pdf=Rahul-Patil-Resume.pdf index.html
```

## Publishing

The repo is static — GitHub Pages serves it as-is from the branch root, no workflow needed.
