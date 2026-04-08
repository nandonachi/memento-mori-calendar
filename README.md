# Memento Mori Calendar

**Your life in weeks. One page. On your wall.**

A printable life calendar that visualizes your entire life as a grid of weeks. Each box is one week. The dark ones are gone. The empty ones are what you might have left. Print it. Put it on your wall. Fill in one box every Sunday.

No install. No accounts. No frameworks. Just one HTML file.

<!-- ![Preview](preview.png) -->

---

## Quick Start

### Option A: Just open it
1. **Download** `index.html`
2. **Double-click** to open in your browser
3. **Enter your date of birth**
4. **Click "Print My Calendar"**
5. **Set paper size to Legal (8.5" x 14")** in the print dialog

### Option B: Run a local server
```bash
# Clone the repo
git clone https://github.com/anchatur/memento-mori-calendar.git
cd memento-mori-calendar

# Serve it (pick one)
python -m http.server 8000        # Python
npx serve .                        # Node.js

# Open http://localhost:8000 in Chrome or Edge
```

That's it. Your life calendar is ready to hang on the wall.

---

## Customization

| Setting | Required | Default | Description |
|---------|----------|---------|-------------|
| Date of Birth | Yes | — | Your birthday. This determines which weeks are marked as "lived." |
| Life Expectancy | No | 80 years | How many rows the grid has. Range: 50–120 years. |
| Quote | No | Marcus Aurelius | The quote displayed above the grid. Leave empty to hide it. |
| Quote Author | No | Marcus Aurelius, Meditations | Attribution shown below the quote. |

### Bookmarkable URLs

Your settings are saved in the URL automatically. Bookmark it or share it:

```
index.html?dob=1990-10-01&years=85&quote=Your+custom+quote&author=Someone
```

---

## Print Setup

This calendar is designed for **Legal paper (8.5" x 14")**. The extra height gives each week-box enough room to mark with a pen.

| Setting | Value |
|---------|-------|
| Paper Size | **Legal (8.5" x 14")** |
| Orientation | Portrait |
| Margins | None |
| Scale | 100% |
| Background Graphics | Enabled |

### Browser Tips

- **Chrome / Edge** — Best results. Set margins to "None" and enable "Background graphics" in More Settings.
- **Firefox** — Works well. Set margins to "None" in Page Setup.
- **Safari** — Set "Print backgrounds" in the print dialog.

The configuration panel automatically hides when printing — only the calendar appears on paper.

---

## Philosophy

*Memento Mori* is Latin for "remember that you will die." It's a practice from Stoic philosophy — not meant to be morbid, but clarifying. By keeping mortality in awareness, you stop taking time for granted.

This calendar makes that idea tangible. Each of the ~4,160 boxes represents one week of an 80-year life. The filled boxes are gone forever. The empty ones are what remains. Seeing your entire life on a single page creates an urgency that no productivity app can match — not anxiety, but *clarity* about how you spend your weeks.

> "You could leave life right now. Let that determine what you do and say and think."
> — Marcus Aurelius, *Meditations*

---

## Technical Details

- **Zero dependencies** — no npm, no build step, no frameworks. Just one self-contained HTML file.
- **Print-first design** — all dimensions are in mm, optimized for legal paper at any DPI.
- **Google Fonts** — uses Cormorant Garamond and Inter. Falls back gracefully to system fonts if offline.
- **Works offline** — after the first load (which fetches fonts), everything runs locally.
- **URL parameters** — configuration is encoded in the URL for bookmarking and sharing.

---

## Contributing

Contributions are welcome! Some ideas:

- **A4 paper support** — alternative layout for international paper sizes
- **Color themes** — dark mode, sepia, custom accent colors
- **Internationalization** — translated labels and date formats
- **Accessibility** — screen reader support, keyboard navigation
- **Browser-specific print fixes** — especially Firefox and Safari edge cases

### Ground Rules

Please keep it simple. This project is intentionally minimal:

- **One HTML file.** No build tools. No frameworks. No package managers.
- **No external JS dependencies.** Vanilla JavaScript only.
- **Print quality matters most.** Every change should be tested in print preview.

---

## License

MIT License. See [LICENSE](LICENSE) for details.

---

*Made with mortality in mind.*
