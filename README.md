# [Unofficial] OIST Doctoral Thesis Typst Template (updated August 14th, 2026)

This is a Typst template for writing a doctoral thesis at the Okinawa Institute of Science and Technology graduate university (OIST).

**This template has NOT received any approval from the OIST GS Examination team. It is NOT officially supported.** In other words, it is an unofficial template created by me personally.
During meetings, I showed the PDF created using this template and incorporated several suggested revisions. However, I reiterate that since this is not an official OIST template, it may not be correct.

If you find any updates or fixes, please contact me (k.takada@oist.jp). You can also use the Issues or Pull Requests in this repository.

## What is Typst?

Faster than latex (in my opinion.) Easier to set up a local environment than LaTeX (in my opinion.)

Typst is a modern, markup-based typesetting system designed to feel as approachable as Markdown while offering the layout control of LaTeX. Documents are written in plain text, compiled with the open-source `typst` tool, and can make full use of reusable components, scripting, and styling primitives. You can learn more at the official documentation: [https://typst.app/docs/](https://typst.app/docs/)

## Prerequisites

### typst
You need to install Typst. You can find the installation instructions for your operating system on the official Typst website: [https://typst.app/docs/guide/install/](https://typst.app/docs/guide/install/)

The current target version is v0.15.1.

### mise
mise is a package manager for local tools. Please visit their [website](https://mise.jdx.dev/) and install it on your computer.  

After installation, please run the following command in the directory where you cloned this repository.

```bash
mise trust
mise install
```

### Fonts

The main text uses Times New Roman and figure captions use Helvetica, both of which are already on macOS and Windows. Everything else the template falls back on — New Computer Modern for the title page, DejaVu Sans Mono for code blocks — ships with the Typst CLI, so there is nothing else to install.

## Usage

To compile the thesis, run the following command in your terminal:

```bash
typst compile main.typ
```

This will generate a PDF file named `main.pdf` in the same directory.

## Structure

- `main.typ`: The main file for your thesis. It imports all the necessary files and sets up the document structure.
- `oist_thesis.typ`: The core template file. It defines the `thesis` function, which sets up the title page, headers, and other document-wide settings.
- `chapters/`: This directory contains the individual chapters of your thesis. You can add, remove, or rename files in this directory as needed.
- `preamble/`: This directory contains the preamble files: the two declarations (original authorship, AI tool use), abstract, acknowledgments, abbreviations, glossary, nomenclature, list of publications, and dedication.
- `images/`: This directory contains the images used in your thesis, including the placeholder signature `images/signature.svg`.
- `bibliography.bib`: The bibliography file for your thesis. You can add your own references to this file.

## Customization

To customize your thesis, you will need to edit the following files:

- `main.typ`: Change the `title`, `author`, `supervisor`, `cosupervisor`, and `submission_date` variables to match your own information. `mode` switches between the 1.5-spaced examination copy (`"draft"` / `"review"`) and the single-spaced final version (`"submission"`), and `colored_refs: true` turns citations and cross-references blue for reading on screen.
- `chapters/`: Edit the files in this directory to write the content of your thesis.
- `preamble/`: Edit the files in this directory to add your own abstract, acknowledgments, and other preamble content. Delete the files you do not need (dedication, glossary, nomenclature, publications, AI tool declaration) along with their `#include` line in `main.typ`.
- `images/signature.svg`: Replace the placeholder with a scan of your own signature. It is embedded on the declaration page by `preamble/declaration.typ`; any image format Typst reads (SVG, PNG, JPG, PDF) works.
- `bibliography.bib`: Add your own references to this file.

Chapter 3 of the compiled template, "How to use the templates", documents the rest: every preamble page, the appendix wrapper, embedding published-article PDFs, and the figure/table helpers.

## Working in VS Code (Reccomendation)

This template works smoothly with the [Tinymist Typst](https://marketplace.visualstudio.com/items?itemName=myriad-dreamin.tinymist). Once the extension is installed:

- Tinymist provides Typst language-server support out of the box, including syntax highlighting, code completion, diagnostics, and formatting.
- Use the command palette (`Cmd+Shift+P` / `Ctrl+Shift+P`) and run Typst Preview: to open a live preview of the current document. You can also use `Ctrl+K V`.
- To generate a PDF, use `Typst Export PDF` or `Typst Show PDF`.... Tinymist can also be configured to export PDFs automatically on save or while typing.
- Alternatively, if the Typst CLI is installed, you can add a VS Code task that runs `typst watch main.typ main.pdf`.

### Sample view

The reason I use typst is that I can work while viewing multiple chapter pages and bib files, and see the compilation results immediately.
![Editor screenshot](editor_screenshot.png)

## License

This template is released under the [MIT No Attribution (MIT-0)](LICENSE) license: you may use, copy, modify, and distribute it, including for your own thesis, without keeping the copyright notice or crediting the author.

The license does not cover the OIST logo and symbol (`images/symbol.jpg`, `images/chap3/emblem.jpg`, `images/chap3/symbol.jpg`). They belong to the Okinawa Institute of Science and Technology and are included only so the template renders as an OIST thesis; use them according to OIST's own rules.
