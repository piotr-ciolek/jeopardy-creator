# Jeopardy Game Creator

A standalone, single-file HTML app for building and running a Jeopardy-style trivia game. No server, build step, or dependencies required — just open the HTML file in a browser.

## Features

- **Two tabs**: a *Creator* tab (game setup, visible only to the host) and a *Game board* tab (full-screen board for players).
- **Bilingual UI**: switch between English and Polish (Va banque) with one click. All labels, buttons, and messages update instantly.
- **Custom game title** shown above the board.
- **CSV or XLSX input**: load your questions from either format.
- **Downloadable templates**: ready-to-edit CSV and XLSX templates, in English or Polish, generated on demand.
- **Full-screen question cards** with large, readable text for question and answer.
- **Click-to-reveal, click-to-remove**: clicking a tile shows the question and permanently removes that tile from the board.

## Usage

1. Open `jeopardy_creator.html` in any modern browser (Chrome, Firefox, Edge, Safari).
2. In the **Creator** tab, optionally download a template (CSV or XLSX) to see the expected format.
3. Set a game title, then choose your completed CSV or XLSX file.
4. The **Game board** tab unlocks automatically once the file passes validation.
5. Switch to the **Game board** tab to run the game for players. Click a tile to reveal its question; use **Reveal answer** to show the answer.
6. Use **Reset game board** to restore all 30 tiles for a new round with the same data.

## File format

Header row: `category,question,answer`

- Exactly **6 distinct categories**.
- Exactly **5 questions per category** (30 rows total).
- Row order within a category sets the point value: 100, 200, 300, 400, 500.
- CSV files must be saved as **UTF-8** (with or without BOM) to correctly display Polish characters.
- For XLSX, put all data on the **first worksheet**.

## Notes

- Everything runs client-side; no data is uploaded anywhere.
- The app has no external dependencies (no CDN scripts, no frameworks) — it's a single portable `.html` file.
