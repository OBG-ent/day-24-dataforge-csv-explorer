# DataForge 🛠️

**Drop a CSV and explore it — search, sort, filter, aggregate, and chart thousands of rows instantly, without uploading your data anywhere.**

Spreadsheets are where data goes to be squinted at. DataForge is a privacy-first CSV explorer that runs **entirely in your browser**: drag in a file and you get a fast, searchable, sortable table with live statistics and group-by charts — whether it's 50 rows or 50,000. Your file never leaves your device, which makes it safe for the exports you'd never paste into a random website.

## ✨ Features

- 📂 **Three ways in** — drag &amp; drop a file, pick one, or paste raw CSV text
- ⚡ **Built-in stress test** — one click generates a deterministic **10,000-row** dataset so you can feel the performance yourself
- 🧮 **A real CSV parser** — correctly handles quoted fields, embedded commas, escaped quotes, and newlines inside cells (the stuff that breaks naive `split(",")` parsers)
- 🔎 **Debounced full-text search** across every column, with match counts
- ↕️ **Click-to-sort columns** — numeric-aware sorting, direction toggle
- 📄 **Paged rendering** — 100 rows per page keeps the DOM fast no matter how big the file gets
- 📊 **Live stat cards** — row/column counts plus sum &amp; average for numeric columns
- 📈 **Group-by chart** — pick a category column and a number column, get a top-10 totals bar chart on Canvas
- ⬇ **Export what you see** — download the current filtered + sorted view as a new CSV
- 🔒 **Private by architecture** — no server, no upload, no tracking; the File API reads locally

## 🚀 Run it in 30 seconds

No build tools, no server needed:

1. Download or clone this repo
2. Double-click **`index.html`** — that's it

**Try this:** hit **⚡ Generate 10,000-row sample**, then search for `Toronto`, sort by `revenue`, and check the chart — it defaults to revenue by city across the full dataset. The whole thing parses and renders in milliseconds.

## 🧠 What I practiced

- Writing a correct CSV tokenizer (quote state machine) instead of splitting on commas
- Performance thinking — paged rendering, debounced search (160ms), sampling for numeric-column detection
- The File API + drag-and-drop events (`dragover`/`drop` with `preventDefault` discipline)
- Type inference — sniffing which columns are numeric (≥80% numeric sample) to drive stats, sorting, and charting
- Aggregation pipelines — group-by totals over the full dataset, independent of the filtered view
- Deterministic pseudo-random data generation (seeded LCG) so the demo is identical for every visitor

## 🗂️ Project structure

```
day-24-dataforge-csv-explorer/
├── index.html   # the whole app — parser, UI, and charts in one file
└── README.md
```

## 🔮 Ideas for v2

- Column filters (per-column dropdowns and ranges)
- JSON file support alongside CSV
- Saved views — remember a search + sort combo per file

---

Day 24 of my daily coding streak — one simple build and one bigger build, every day. Follow along: [@Reynoldobago](https://x.com/Reynoldobago) · [github.com/OBG-ent](https://github.com/OBG-ent)
