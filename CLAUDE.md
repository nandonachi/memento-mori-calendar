# CLAUDE.md

## What is this?

A single-file, printable "Memento Mori" life calendar. It visualizes an entire human life as a grid of weeks (52 columns × N rows), designed to be printed on US Legal paper (8.5" × 14") and hung on a wall.

The entire project is one HTML file: `index.html`. No build tools, no dependencies, no frameworks.

## How to run it

```bash
# Option 1: Python (most systems have this)
python -m http.server 8000

# Option 2: Node.js
npx serve .

# Option 3: Just open the file directly
# On macOS:
open index.html
# On Windows:
start index.html
# On Linux:
xdg-open index.html
```

Then open http://localhost:8000 (for options 1/2) in a browser. Chrome or Edge give the best print results.

## How it works

1. User opens the page and sees a **config panel** at the top (date of birth, life expectancy, quote, author)
2. Entering a DOB **live-renders** the calendar grid below — no page reload needed
3. Config is encoded in **URL parameters** (`?dob=2000-01-15&years=80`) for bookmarking/sharing
4. Clicking **"Print My Calendar"** triggers `window.print()` — the config panel is hidden via `@media print`, only the calendar prints
5. Calendar is sized in **mm units** to fit exactly on one US Legal page

## Architecture

```
index.html          ← Everything lives here. ~400 lines total.
├── <style>         ← CSS: config panel styles, calendar print layout, screen/print media split
├── <body>
│   ├── .config-panel    ← Form inputs (DOB, years, quote, author) + Print button
│   ├── .config-divider  ← Visual separator (hidden in print)
│   └── .calendar-page   ← The printable calendar
│       ├── .header          (title + ornament)
│       ├── .quote-section   (dynamic quote text)
│       ├── .legend          (lived/remaining key)
│       ├── .grid-container  (year labels + week headers + the grid)
│       │   └── .grid        (background-color-as-gridlines technique — no borders on cells)
│       ├── .footer          (instructions + birth info)
│       └── .empty-state     (shown when no DOB entered)
└── <script>        ← Vanilla JS: renderCalendar(), URL param read/write, event listeners
```

### Key design decisions

- **Grid rendering trick**: The `.grid` container has a `#ddd` background with `gap: 1px`. Each `.cell` is a solid-colored div. The container background shows through the gaps = perfectly uniform grid lines. No per-cell borders = no sub-pixel rounding issues in print.
- **mm units for print**: Cell sizes are in mm (not px) so they map predictably to physical paper at any DPI.
- **`@page { margin: 0 }`**: The HTML controls all spacing. No browser-added margins.
- **`overflow: hidden` in print**: Prevents any content spilling to a second page.

## Constraints (do not violate)

- **Single HTML file** — everything must stay in `index.html`. No separate CSS/JS files.
- **No external JS dependencies** — vanilla JavaScript only. Google Fonts is the only external resource.
- **No build tools** — no npm, webpack, vite, etc. The file must work by double-clicking it.
- **Print quality is the #1 priority** — every change must be verified in print preview on Legal paper.
- **Legal paper (216mm × 356mm)** — the calendar is dimensioned for this exact size.

## Testing a change

1. Open `index.html` in Chrome
2. Enter a DOB → verify grid renders with correct weeks lived
3. Change life expectancy → verify row count changes
4. Change quote → verify it updates on the calendar
5. Clear DOB → verify empty state appears
6. Open print preview (Ctrl+P / Cmd+P):
   - Paper size: Legal
   - Margins: None
   - Background graphics: ON
   - Verify: config panel is NOT visible, calendar fits on exactly 1 page, grid lines are uniform
7. Test URL params: reload with `?dob=2000-01-15&years=90` → form should pre-fill correctly

## File overview

| File | Purpose |
|------|---------|
| `index.html` | The entire application — config UI + printable calendar |
| `README.md` | User-facing docs: quick start, customization, print setup, philosophy |
| `CLAUDE.md` | This file — project context for AI assistants |
| `LICENSE` | MIT license |
| `.gitignore` | OS junk files |
