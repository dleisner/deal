# DEALAMP

A song frequency dashboard for [DEAL](https://www.dealgodown.com), a Seattle-based Grateful Dead tribute band. Tracks the last 12 shows: setlists, play counts, segues, and days since each song was last played.

Live at: `https://dleisner.github.io/deal/`

## What it shows

- **Stats** — total shows, sets, unique songs played, total plays, songs/set
- **Show buttons** — tap any of the 12 shows to view its full setlist and highlight that show's column in the song grid
- **Song list** — every song in the DEAL repertoire, sortable by frequency or alphabetically, with:
  - Play count in the last 12 shows
  - Days since last played (computed live each visit)
  - Colored dots showing exactly which shows the song was played at
- **Canonical not-yet-played** — songs marked with `*` are Grateful Dead canon that DEAL hasn't yet added to their repertoire

## How it works

`index.html` is a self-contained file. No build step, no dependencies, no database. All setlist data lives as JavaScript literals at the top of the `<script>` block. Days-since values are calculated at render time from `new Date()`, so the page is always current without needing to be regenerated.

The 12-show window is hardcoded. When a 13th show is added, the oldest drops off.

## Deployment

GitHub Pages, free tier. Settings → Pages → Deploy from `main` branch, root.

## Notes

- Designed for iPhone portrait (390px max-width). Works on desktop but optimized for mobile.
- Public URL with no authentication. Don't put anything sensitive in setlist data.
- Source of truth for setlist data is DEALBASE (SQLite, maintained separately). This HTML is a snapshot view; the DB is canonical.
