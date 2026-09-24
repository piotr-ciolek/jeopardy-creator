# Jeopardy! / Va banque! Game Creator

A standalone, single-file HTML app for building and running a Jeopardy-style trivia game. No server, build step, or dependencies required — just open the HTML file in a browser.

> **AI-generated project.** This app (code and this README) was generated with the help of an AI assistant. Review it before relying on it for anything important.

## Features

- **One page, two modes**: toggle **Editable mode** on the fly. Off = play mode (click a tile, see the question, tile disappears). On = build mode (rename categories, click any tile to edit its question, answer, image, and link).
- **Bilingual UI**: switch between English ("Jeopardy!") and Polish ("Va banque!") with one click. All labels, buttons, and messages update instantly.
- **Custom game title**, editable in editable mode.
- **CSV or XLSX import**: load 6 categories × 5 questions from either format. Downloadable templates (CSV and XLSX, in either language) available in editable mode.
- **Per-question images**: attach an optional image to any question while editing; it shows on the question card once revealed, with no visual hint on the board tile beforehand.
- **Per-question links**: attach an optional named hyperlink (e.g. a YouTube clip) to any question; it appears as a clickable button on the question card.
- **Shareable links**: generate a link (via the 🔗 Share button) that encodes the entire board — title, categories, questions, answers, links, and progress — into the URL hash. Opening the link restores the game automatically; images can optionally be included (off by default, since it can make the link very long).
- **Full-screen question cards** with large, readable text.

## Usage

1. Open the HTML file in any modern browser.
2. Turn on **Editable mode** to import a file, download a template, set the title, or click any category/tile to type questions, answers, images, and links directly.
3. Turn **Editable mode** off to play: click a tile to reveal its question, then **Reveal answer**. Use **Reset game board** to restore all tiles for a new round.
4. Use **🔗 Share** to get a link that saves/bookmarks the current state, or to share the game with others.

## File format (CSV / XLSX)

Header row: `category,question,answer`

- Exactly **6 distinct categories**, exactly **5 questions per category** (30 rows).
- Row order within a category sets the point value: 100, 200, 300, 400, 500.
- CSV files must be **UTF-8** (with or without BOM) for Polish characters to display correctly.
- For XLSX, put all data on the **first worksheet**. Images and links aren't part of the file format — add them afterward in editable mode.

## Notes

- Everything runs client-side; no data is uploaded anywhere.
- No external dependencies (no CDN scripts, no frameworks) — a single portable `.html` file.
