# Jeopardy! / Va banque! Game Creator

A standalone, single-file HTML app for building and running a Jeopardy-style trivia game. No server or dependencies — just open the HTML file in a browser.

> **AI-generated project.** Review before relying on it for anything important.

## Features

- **Editable mode** (top right): build mode with a **ⓘ help button** (top left) showing quick step-by-step instructions.
- **Two rounds**: **Round 1** (6×5 grid) and **Final** (one glowing tile) — tabs sit to the right of the title.
- **Bilingual**: English ("Jeopardy!") / Polish ("Va banque!"), one click to switch.
- **Countdown timer**: 3–300 seconds, shown as a badge; stops on Reveal answer.
- **Images**: auto-resized and compressed.
- **Audio**: attach a clip (up to 8 MB, not compressed) with:
  - **Autoplay** (default on) — plays the instant the question is revealed.
  - **Start at** — a checkbox + `MM:SS` field (like YouTube). Drag the audio preview's own player while editing to set the value automatically; typed values are normalized on blur (e.g. `0:72` → `1:12`). Unchecked = always starts at `0:00`.
- **Links**: an optional named hyperlink shown as a button on the question.
- **CSV/XLSX import & export**: 6 categories × 5 questions, plus one `Final` row for the Final question. Optional columns: `image`, `audio`, `audio_start`, `audio_autoplay`, `link_label`, `link_url`.
- **🔗 Share link**: encodes a snapshot of the whole board (incl. Final and progress) into the URL; images/audio only if you check "include images and audio" (long clips make long links).
- **Full-screen question cards** with a scroll region that keeps action buttons always visible.

## Sharing: file vs. link

| | Export (CSV/XLSX) | 🔗 Share link |
|---|---|---|
| Length limit | None | Yes — long links can fail elsewhere |
| Best for | Games with media, backups | Quick sharing, incl. progress |
| Stays current | No — re-export after changes | No — one-time snapshot |

If your game has images or audio, **prefer Export** for reliability. Clicking Share also updates the address bar, but only as a snapshot — it won't reflect later edits until you click Share again.

## Usage

1. Open the HTML file. Click **ⓘ** any time for in-app instructions.
2. Turn on **Editable mode**, import a file or click a tile to fill in a question (and optionally an image, audio, or link).
3. Turn **Editable mode** off to play; click a tile to reveal it.
4. Use **Export** or **🔗 Share** to save or send your game.

## File format (CSV / XLSX)

- Required: `category,question,answer`. Exactly 6 categories × 5 rows (30 rows).
- One optional row with category `Final` (any case) is the Final question.
- Only `category` is required per row — blank question/answer is fine (work in progress).
- CSV must be UTF-8. XLSX data goes on the first worksheet.
- Optional columns: `image`, `audio`, `audio_start` (seconds), `audio_autoplay` (`true`/`false`), `link_label`, `link_url`. Missing columns/rows just default to blank — older files keep working.

## Notes

- Everything runs client-side; nothing is uploaded anywhere.
- No dependencies — a single portable `.html` file.
