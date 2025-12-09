# GitHub Action: Build LaTeX PDF (via Docker)

This GitHub Action compiles `.tex` documents into PDF or other LaTeX output formats using the public Docker image:

https://hub.docker.com/r/basemax/latex-builder

This action removes the need to install TeX Live on GitHub runners by using a fully isolated, reproducible Docker environment.

---

## Features

- Uses Docker image `basemax/latex-builder:latest`
- Supports multiple formats:
  - pdf
  - dvi
  - ps
  - slides
  - beamer (presentations)
  - clean (remove temp files)
- Secure and reproducible builds
- Supports optional custom output filename
- Zero LaTeX installation required

---

## Inputs

| Name         | Required | Default | Description |
|--------------|----------|---------|-------------|
| `tex_path`   | Yes      | —       | Path to `.tex` file |
| `build_format` | No    | pdf     | pdf, dvi, ps, slides, beamer, clean |
| `output_path` | No     | auto    | Custom output PDF |

---

## Outputs

| Output | Description |
|--------|-------------|
| `pdf` | Path to generated PDF file |

---

## Example: Basic PDF Build

```
jobs:
build:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v4
  - name: Build PDF
    uses: BaseMax/github-actions-build-latex-pdf@v1
    with:
      tex_path: "main.tex"
```

---

## Example: Presentation Build

```
* uses: BaseMax/github-actions-build-latex-pdf@v1
  with:
  tex_path: "slides.tex"
  build_format: "beamer"
```

---

## Example: Custom Output Name

```
* uses: BaseMax/github-actions-build-latex-pdf@v1
  with:
  tex_path: "doc/report.tex"
  output_path: "output/final-report.pdf"
```

---

## Docker Image Used

This Action uses:

```
basemax/latex-builder:latest
```

The image supports:

| Mode | Output |
|------|--------|
| pdf | PDF document |
| dvi | Device Independent file |
| ps | PostScript |
| slides | Slide PDF |
| beamer | Presentation PDF |
| clean | Remove temp files |

---

## License

MIT License  

Copyright © 2025 Seyyed Ali Mohammadiyeh (Max Base)
