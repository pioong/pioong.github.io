# pioong.github.io — Claude Instructions

## Project overview
This is Pio Ong's academic personal website, hosted on GitHub Pages. It is a single file: `index.html`.

## Folder structure
```
Documents/claude/
├── pioong.github.io/   ← this website (index.html)
└── cv/
    ├── PO_bold.bib     ← master bibliography (source of truth for publications)
    ├── alias.bib       ← venue abbreviation definitions (e.g., cdc, acc, csl, tac)
    ├── CV_PO.tex       ← CV LaTeX source
    └── Publication.tex ← publication list LaTeX source
```

## Updating publications

When Pio says "I updated my CV / bib, update the publications", do the following:

1. Read `../cv/PO_bold.bib` and compare it against the current publications section in `index.html` (starts at line ~965, `id="publications"`).
2. Identify any entries in the bib that are missing from the website.
3. Add them to the correct section (Journal Papers or Conference Papers) in reverse chronological order (newest first, since the list uses `<ol reversed>`).
4. **Always ask Pio for the arXiv URL** for each new entry before making any edits. Do not proceed with updating index.html until the URL is provided.

### HTML format for each publication entry

**Journal paper:**
```html
<li class="mb-2"> <b>P. Ong</b>, A. Author, B. Author. <a href="https://arxiv.org/abs/XXXX.XXXXX">Title of paper</a> <br /> <i>Journal Name</i>, vol:pages, year.
  <br />
</li>
```

**Conference paper:**
```html
<li class="mb-2"> <b>P. Ong</b>, A. Author, B. Author. <a href="https://arxiv.org/abs/XXXX.XXXXX">&ldquo;Title of paper&rdquo;</a> <br /> Proceedings of the <i>Conference Name</i>, City, Country, Month Year. pp. XXXX-XXXX.
  <br />
</li>
```

**Status notes:**
- `note = {Submitted}` → replace pages with "Submitted."
- `note = {To Appear}` → replace pages with "To Appear."
- No note → use actual page numbers

### Author formatting rules
- `\textbf{P. Ong}` → `<b>P. Ong</b>` in HTML
- LaTeX special chars: `{B}oolean` → `Boolean`, `\'e` → `é`, `\&` → `&amp;`, `$...$` → plain text
- Journal papers: authors listed as "A. Author, B. Author." (no quotes around title, title is a plain link)
- Conference papers: title wrapped in `&ldquo;...&rdquo;` (curly quotes)

### Venue abbreviations (from alias.bib)
| Abbreviation | Full name |
|---|---|
| `csl` | IEEE Control Systems Letters |
| `tac` | IEEE Transactions on Automatic Control |
| `automatica` | Automatica |
| `acc` | American Control Conference |
| `cdc` | IEEE Conference on Decision and Control |
| `iros` | IEEE/RSJ International Conference on Intelligent Robots and Systems |
| `ifacwc` | IFAC World Congress |

## News section
The news section (id="news") is updated separately from the publications list — it contains timestamped cards about recent submissions, acceptances, and travel. Update it independently when Pio asks.

When adding new submission cards, use the `bg-submitted text-light` card style with the `bi-journal-arrow-down` icon. For multiple papers, do NOT list the individual paper titles — just say "We have submitted X papers to [Venue]." Add arXiv buttons ("See Paper 1", "See Paper 2", ...) only for papers that have links. Always update the "Last updated" date at the top of the news section. Add new cards to the top of `#news-archive` (not `#news-visible`).

## Deployment
After editing `index.html`, commit and push to the `main` branch on GitHub. GitHub Pages auto-deploys from `main`.
Git commit and push are pre-approved — no need to ask for confirmation.
