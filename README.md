# UII Beamer Template

An unofficial LaTeX Beamer presentation template for **Universitas Islam Indonesia (UII)**, adapted from the [UIC Beamer Template](https://github.com/usamamuneeb/uic-beamer-template) by Usama Muneeb.

---

## Requirements

- A LaTeX distribution: [TeX Live](https://www.tug.org/texlive/) (recommended) or [MiKTeX](https://miktex.org/)
- **XeLaTeX** compiler — required for the bundled custom fonts (Open Sans, IBM Plex Serif, etc.)
- Alternatively, **pdfLaTeX** can be used, but the custom fonts will not be applied

## Compilation

```bash
xelatex main.tex
```

Run twice if cross-references or page labels change between passes. If you use a reference slide with citations, also run `bibtex main` between the two XeLaTeX passes.

Most editors (TeXstudio, VS Code with LaTeX Workshop, Overleaf) can be configured to use XeLaTeX automatically.

---

## Project Structure

```
├── main.tex                        # Root document — edit title, author, theme here
├── beamerthemeuii.sty              # Beamer theme (layout, colors, environments)
├── uiicolor.sty                    # UII color definitions
├── uiifont.sty                     # Font setup (XeLaTeX / pdfLaTeX)
│
├── fonts/                          # Bundled OpenType fonts
│   ├── Open_Sans/
│   ├── IBM_Plex_Serif/
│   ├── Noto_Sans_Mono/
│   └── Playfair_Display_SC/
│
├── images/                         # UII logos and background images
│
├── slides/
│   ├── front_matter/
│   │   └── title.tex               # Title slide metadata (title, author, date)
│   ├── main_matter/
│   │   ├── slides1.tex             # Content slides — add more as slides4.tex, etc.
│   │   ├── slides2.tex
│   │   ├── slides3.tex
│   │   └── assets/                 # Images used by main matter slides
│   └── back_matter/
│       ├── slide1.tex              # Thank You slide
│       └── slide2.tex              # References slide
│
└── ref/
    └── ref.bib                     # BibTeX bibliography
```

### Adding slides

Main matter slides are auto-loaded in numeric order. To add new slides, create `slides4.tex`, `slides5.tex`, … inside `slides/main_matter/`. Back matter slides follow the same pattern: `slide3.tex`, `slide4.tex`, … inside `slides/back_matter/`.

---

## Customisation

### Title slide

Edit `main.tex` to set your presentation metadata:

```latex
\title{Your Presentation Title}
% \subtitle{Optional subtitle}
\author{\href{mailto:you@uii.ac.id}{Your Name}}
\date{\today}
\titlebackground*{images/uii_lockup.png}
```

### Theme colors

Two global theme modes are available:

| Command | Background | Text | Logo |
|---|---|---|---|
| `\themecolor{light}` | White | Dark gray | Blue UII logo |
| `\themecolor{dark}` | UII Blue | White | White UII logo |
| `\themecolor{lightnologo}` | White | UII Blue | Hidden (for slides with built-in logo) |

Call `\themecolor{...}` before a `\begin{frame}` to change the look of that frame and all subsequent ones.

### Footer color

```latex
\footlinecolor{uiiblue}          % colored bar + white page numbers (default)
\footlinecolor[steelgray]{white} % white bar + dark page numbers
\footlinecolor{}                 % no footer bar
```

### UII colors

Defined in `uiicolor.sty` and available throughout the document:

| Name | Description |
|---|---|
| `uiiblue` | UII primary blue |
| `uiired` | UII primary red |
| `chicagoblue` | Secondary blue |
| `uihteal` | Secondary teal |
| `championsgold` | Secondary gold |
| `expowhite` | Neutral off-white |
| `steelgray` / `steelgrey` | Neutral dark gray |

---

## Slide Environments

### Standard frame

```latex
\begin{frame}{Frame Title}
\framesubtitle{Optional subtitle}
% content
\end{frame}
```

### Section divider (`chapter`)

```latex
\begin{chapter}[images/Beranda-2-1.png]{uiiblue}{Section Title}
\textit{Optional section subtitle}
\end{chapter}
```

Arguments: `[background image]` (optional), `{background color}`, `{title}`.

### Side-picture frame (`sidepic`)

```latex
\begin{sidepic}{images/your_image.png}{Frame Title}
% content occupies the left 60%
\end{sidepic}
```

### Colored block (`colorblock`)

```latex
\begin{colorblock}[black]{uihteal}{Block Title}
Block content here.
\end{colorblock}
```

Arguments: `[text color]` (optional, default white), `{background color}`, `{title}`.

---

## Fonts

| Role | Font | Used for |
|---|---|---|
| Sans-serif (default) | Open Sans | Body text, titles |
| Serif | IBM Plex Serif | Math (with `\usefonttheme[onlymath]{serif}`) |
| Monospace | Noto Sans Mono | Verbatim / code |
| Small caps | Playfair Display SC | Pseudocode small caps |

To switch the entire presentation to serif mode, change `\usefonttheme[onlymath]{serif}` to `\usefonttheme{serif}` in `main.tex`.

---

## Credits

- Original template: [UIC Beamer Template](https://github.com/usamamuneeb/uic-beamer-template) by Usama Muneeb
- Adapted for Universitas Islam Indonesia (UII)
- Fonts: Open Sans, IBM Plex Serif, Noto Sans Mono (SIL OFL), Playfair Display SC (SIL OFL)
