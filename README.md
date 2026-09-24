# Jeopardy! / Va banque! Game Creator

A standalone, single-file HTML app for building and running a Jeopardy-style trivia game. No server, build step, or dependencies required — just open the HTML file in a browser.

> **AI-generated project.** This app (code and this README) was generated with the help of an AI assistant. Review it before relying on it for anything important.

## Features

- **One page, two modes**: toggle **Editable mode**. Off = play mode (click a tile, see the question, tile disappears). On = build mode (rename categories, click any tile to edit its question, answer, image, and link).
- **Bilingual UI**: English ("Jeopardy!") and Polish ("Va banque!"), switchable with one click.
- **Countdown timer**: optional per-question timer (3–300 seconds, default 30) shown as a clock-style `M:SS` badge on the question card. Starts automatically when a tile is opened; turns red and bounces at zero; stops instantly when you click Reveal answer. Configurable in Editable mode; it's a live session setting, not saved to exported files or share links.
- **CSV or XLSX import**: load 6 categories × 5 questions.
- **Per-question images**: automatically resized (max ~900 px) and compressed to JPEG in the browser to keep files and links small.
- **Per-question links**: an optional named hyperlink (e.g. a YouTube clip), shown as a button on the question card.
- **Export game as CSV/XLSX**: saves the *entire current board* — including images and links — to a real file.
- **Shareable link**: the 🔗 Share button encodes a snapshot of the board into the URL. Convenient, but has real limits — see below.
- **Full-screen question cards** with large, readable text.

## Two ways to share a game

| | Export as CSV/XLSX | 🔗 Share link |
|---|---|---|
| Where the data lives | In a downloaded file | Inside the URL text |
| Length limit | None in practice | Yes — URLs have hard limits |
| Best for | Games with images, backups | Quick sharing of small/no-image games |
| Progress included | No — questions only | Yes — including which tiles were played |
| Stays up to date? | You export again when you change things | No — it's a one-time snapshot; generate a new link after changes |

**If your game has images, prefer Export.** A URL is only text; embedding an image means putting a compressed, encoded copy of it inside the link, which works for small images but can fail in some browsers or chat apps for large/many images — a limit that can't be worked around from inside a browser. A CSV/XLSX file has no such limit: images are stored as plain text (a `data:image/...;base64,...` value) in an `image` column.

**About the Share link and your browser's address bar:** clicking Share also updates the current page's address bar to match the link at that moment. This is a one-time snapshot, not a live connection — if you keep editing or playing afterward, the address bar (and any bookmark you saved from it) still points to the old state. Click Share again any time to get a fresh link/bookmark for the current state.

## Usage

1. Open the HTML file in any modern browser.
2. Turn on **Editable mode** to import a file, set the title/timer, or click any category/tile to edit it.
3. To save or share a finished (or in-progress) game with images, use **Export as CSV/XLSX**, then send that file however you like. Re-importing it via **Choose CSV or XLSX** restores everything.
4. Turn **Editable mode** off to play: click a tile to reveal its question (the timer starts automatically if enabled), then **Reveal answer** to stop the timer and see the answer. **Reset game board** restores all tiles for a new round.
5. Use **🔗 Share** for a quick snapshot link — fine for text-only or lightly-illustrated games; for images, prefer Export.

## File format (CSV / XLSX)

Required header columns: `category,question,answer`.

- Exactly **6 distinct categories**, exactly **5 rows per category** (30 rows total).
- Row order within a category sets the point value: 100, 200, 300, 400, 500.
- Only the **category** name is required per row — question and answer may be blank (an unfinished tile). This is intentional, so you can export and re-import a work-in-progress game.
- CSV files must be **UTF-8** (with or without BOM) for Polish characters to display correctly.
- For XLSX, put all data on the **first worksheet**.
- **Optional columns**: `image`, `link_label`, `link_url`. Files exported by the app include these automatically; files without them simply have no images/links. The blank "Download template" files only include the 3 required columns.

## Notes

- Everything runs client-side; no data is uploaded anywhere.
- No external dependencies (no CDN scripts, no frameworks) — a single portable `.html` file.
