# Jeopardy! / Va banque! Game Creator

A standalone, single-file HTML app for building and running a Jeopardy-style trivia game. No server, build step, or dependencies required — just open the HTML file in a browser.

> **AI-generated project.** This app (code and this README) was generated with the help of an AI assistant. Review it before relying on it for anything important.

## Features

- **One page, two modes**: toggle **Editable mode**. Off = play mode (click a tile, see the question, tile disappears). On = build mode (rename categories, click any tile to edit its question, answer, image, and link).
- **Two rounds**: a **Round 1** tab (the usual 6×5 grid) and a **Final** tab — a single, glowing tile covering the whole board. Clicking it opens the same reveal flow (image, link, timer, Reveal answer) as any other question; editing it works the same way too. The round tabs sit to the right of the game title.
- **Bilingual UI**: English ("Jeopardy!") and Polish ("Va banque!"), switchable with one click.
- **Countdown timer**: optional per-question timer (3–300 seconds, default 30) shown as a badge on the question card. Starts automatically when a tile is opened; turns red and bounces at zero; stops the instant you click Reveal answer. Configurable in Editable mode; it's a live session setting, not saved to exported files (it *is* remembered by 🔗 Share links).
- **CSV or XLSX import/export**: 6 categories × 5 questions for Round 1, plus the Final question in one extra row (see below).
- **Per-question images**: automatically resized (max ~900 px) and compressed to JPEG in the browser to keep files and links small.
- **Per-question links**: an optional named hyperlink (e.g. a YouTube clip), shown as a button on the question card.
- **Export game as CSV/XLSX**: saves the *entire current board* — Round 1 and Final, including images and links — to a real file.
- **Shareable link**: the 🔗 Share button encodes a snapshot of the whole board (Round 1 and Final) into the URL. Convenient, but has real limits — see below.
- **Full-screen question cards** with large, readable text, and a scroll region that keeps the Reveal/Save buttons always visible even for very long questions.

## The Final round

- Switch to it with the **Final** tab, next to the game title on the right.
- It shows one large tile instead of a 6×5 grid — same font as the point tiles, no italics, both words the same size; a soft glow animation is what marks it as special.
- Click it to reveal the question — identical behavior to a normal tile: image, link button, countdown timer, Reveal answer.
- In Editable mode, click the tile to edit its question, answer, image, and link, exactly like any other tile.
- **In CSV/XLSX files**, the Final question is one extra row using the reserved category name `Final` (case-insensitive) — see the file format section below. It's also included in 🔗 Share links.

## Two ways to share a game

| | Export as CSV/XLSX | 🔗 Share link |
|---|---|---|
| Where the data lives | In a downloaded file | Inside the URL text |
| Length limit | None in practice | Yes — URLs have hard limits |
| Includes the Final question | Yes | Yes |
| Best for | Games with images, backups | Quick sharing, including current progress |
| Progress included | No — questions only | Yes — including which tiles (and Final) were already played |
| Stays up to date? | You export again when you change things | No — it's a one-time snapshot; generate a new link after changes |

**If your game has images, prefer Export.** A URL is only text; embedding an image means putting a compressed, encoded copy of it inside the link, which works for small images but can fail in some browsers or chat apps for large/many images — a limit that can't be worked around from inside a browser. A CSV/XLSX file has no such limit.

**About the Share link and your browser's address bar:** clicking Share also updates the current page's address bar to match the link at that moment. This is a one-time snapshot, not a live connection — if you keep editing or playing afterward, the address bar (and any bookmark you saved from it) still points to the old state. Click Share again any time for a fresh link/bookmark.

## Usage

1. Open the HTML file in any modern browser.
2. Turn on **Editable mode** to import a file, set the title and timer, or click any category/tile (Round 1 or Final) to edit it.
3. To save or share a finished (or in-progress) game with images, use **Export game as CSV/XLSX**, then send that file however you like. Re-importing it via **Choose CSV or XLSX** restores everything, Final question included.
4. Turn **Editable mode** off to play: click a tile to reveal its question (the timer starts automatically if enabled), then **Reveal answer**. **Reset game board** restores all Round 1 tiles and the Final tile for a new round.
5. Use **🔗 Share** for a quick snapshot link that includes everything; for image-heavy games, prefer Export.

## File format (CSV / XLSX)

Required header columns: `category,question,answer`.

- Exactly **6 distinct categories**, exactly **5 rows per category** (30 rows) for Round 1.
- Row order within a category sets the point value: 100, 200, 300, 400, 500.
- **One optional extra row** with category `Final` (any case, e.g. `final`, `FINAL`) holds the Final question — question/answer/image/link work exactly the same as any other row. At most one such row is allowed. Files without it simply leave the Final question blank (older exports/templates keep working).
- Only the **category** name is required per row — question and answer may be blank (an unfinished tile). This is intentional, so you can export and re-import a work-in-progress game.
- CSV files must be **UTF-8** (with or without BOM) for Polish characters to display correctly.
- For XLSX, put all data on the **first worksheet**.
- **Optional columns**: `image`, `link_label`, `link_url`. Files exported by the app include these automatically; files without them simply have no images/links. The blank "Download template" files include a sample `Final` row too.

## Notes

- Everything runs client-side; no data is uploaded anywhere.
- No external dependencies (no CDN scripts, no frameworks) — a single portable `.html` file.
