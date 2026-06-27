# PagesPerRow

**English** | [繁體中文](README.zh-TW.md)

A PDF reader built around one idea: see many pages at once, in a single row.

Most PDF viewers show one or two pages at a time. PagesPerRow lets you set how many pages sit side-by-side on each row — 4, 6, 8, whatever your screen fits — so you can take in a whole paper at a glance instead of scrolling page by page. It's a bird's-eye reading mode for people who think about a document spatially before they read it linearly.

It's a **single HTML file**. No install, no build, no server, no account. Open it, drag a PDF in, done. Your file never leaves your machine — everything runs locally in the browser.

## Why this exists

If you read academic papers as PDFs, you've probably wanted to scan the overall structure — where the figures are, how long each section runs, where the references start — without committing to a linear page-by-page crawl. Existing tools don't really give you that:

- **Adobe Acrobat** has a thumbnail sidebar, but it's a narrow navigation strip, not a readable high-density layout you actually work in.
- **sioyek**, the popular reader for textbooks and papers, supports single- and two-page modes only. Multiple open issues request three-or-more pages per row (the equivalent of Zathura's `pages_per_row`); as of writing, it isn't implemented.
- **Grid-view PDF editors** show a scrollable wall of thumbnails — useful for reordering pages, but not a tunable reading layout with a fixed number of pages per row.

PagesPerRow fills that specific gap: a configurable number of pages per row, optimised for reading and overview rather than thumbnail navigation.

## Features

- **Configurable pages per row** — a slider from 1 to 8 (default 4); the grid reflows instantly to fit.
- **Independent zoom** — a 10%–200% zoom slider, or **fit-to-grid** mode that auto-sizes pages to the current column count. Switch back to auto anytime with the **Fit** button.
- **Single-page modal** — click any page to blow it up full-screen for detail, with **selectable text** (copy straight out of the PDF). Arrow keys (←/→) flip pages; click the dark area outside the page or press **Esc** to close.
- **Full-text search** — find any text across the whole document. Matching pages get a count badge, every hit is highlighted on the page (in both the grid and the enlarged view), and you can jump between matches from the toolbar.
- **Sharp on Retina** — pages render at device pixel ratio, so text stays crisp when you zoom in.
- **Local & private** — pure front-end, no upload, no backend. PDF.js is loaded from a CDN; your document is read entirely in-browser.

> Status: early / personal project. Built to scratch my own itch reading research papers. Feedback and issues welcome.

## Usage

**Option A — just open the file:**

1. Download [`index.html`](index.html).
2. Open it in any modern browser (Chrome, Firefox, Safari, Edge).
3. Drag a PDF onto the window, or click to pick one.

**Option B — host it:** drop `index.html` on any static host (GitHub Pages, Netlify, an S3 bucket) and bookmark the URL.

Either way you need an internet connection the first time, since PDF.js loads from a CDN.

### Controls

| Action | How |
|---|---|
| Load a PDF | Drag the file onto the window, or click the drop area to browse |
| Pages per row | **Pages-per-row slider** (1–8) in the toolbar |
| Zoom | **Zoom slider** (10%–200%), or the **Fit** button for auto-sizing |
| Enlarge one page | Click the page |
| Flip pages (in modal) | **←** / **→** |
| Select / copy text (in modal) | Drag across the text as usual |
| Close the enlarged page | **Esc**, or click the dark area outside the page |
| Search text | Type in the search box, or **Cmd/Ctrl+F** to focus it |
| Jump between matches | **Enter** / **Shift+Enter**, or the **‹ ›** buttons |

The toolbar shows the file name, the current pages-per-row and zoom values, and the total page count.

## Roadmap

Possible future directions (nothing promised):

- Jump-to-page input and keyboard row scrolling
- Per-document layout memory (remember pages-per-row and zoom per file)
- Lazy rendering for very large PDFs (only render pages in view)
- Book mode (first page single, then paired spreads)
- Smarter search: match across line/word breaks, regex, whole-word
- Annotation and highlight editing — deliberately out of scope for now; this is an overview/reading tool, not an editor.

## Tech

Plain HTML/CSS/JS in one file, no framework. Rendering is handled by [PDF.js](https://mozilla.github.io/pdf.js/) (loaded from cdnjs as an ES module). Pages render asynchronously to `<canvas>` without blocking the UI, and in-flight renders are cancelled when you change zoom or column count.

## Contributing

Issues and pull requests are welcome. If you've hit the same "I just want to see more pages at once" wall in other readers, this is the place to talk about it.

## License

[MIT](LICENSE)
