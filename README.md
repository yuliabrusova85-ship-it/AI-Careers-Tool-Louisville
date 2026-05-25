# AI Career Tools Workshop Simulator

A single-file browser application built for **University of Louisville Libraries** to teach students how to use AI responsibly in their job search. Designed for library instruction sessions and career readiness workshops.

## Live Use

Open `ai-career-tools-workshop.html` in any browser — no server, no install, no internet required (Chart.js loads from CDN on first use).

## Features

### Tab 1 — Resume Review
- Paste resume text and analyze against two competency frameworks:
  - **NACE Career Readiness Competencies** (8 competencies)
  - **KYCPE 10 Essential Employability Skills** (10 competencies)
- Keyword matching with stemming variants (-ing, -ed, -s, -tion, -ly)
- Score classification: Needs Development / Good Foundation / Strong
- Chart.js bar chart showing keyword hits per competency
- Per-competency found/missing breakdown with matched keyword tags
- Auto-generated AI prompt targeting missing competencies

### Tab 2 — Interview Prep
- 15 common behavioral interview questions
- STAR method framework (Situation / Task / Action / Result)
- Four text areas for drafting answers
- Generates a copyable ChatGPT/Claude practice feedback prompt
- Download STAR answers as a .txt file

### Tab 3 — LinkedIn Optimizer
- 20-item checklist across 5 profile categories
- Live score with color-coded progress bar (0–50% red / 51–75% amber / 76–100% green)
- Generates a personalized AI optimization prompt listing unchecked items

### Global
- `localStorage` persistence — work is restored on reopen
- **Export My Work** — downloads a full summary of all three tabs as .txt
- **Clear All Data** — wipes localStorage and resets all inputs
- Mobile-responsive layout
- Print-friendly CSS
- WCAG 2.1 AA accessible (labeled inputs, keyboard nav, focus rings, no color-only cues)

## Branding

Matches University of Louisville visual identity:
- Cardinal Red `#AD0000` header, active tabs, primary buttons, chart bars
- Black tab nav bar, secondary buttons
- Clean Helvetica Neue / Arial sans-serif typography
- Light gray `#F5F5F5` result cards, `#E0E0E0` borders

## Tech Stack

| Layer | Choice |
|-------|--------|
| Structure | Vanilla HTML5 |
| Styling | Embedded CSS (no framework) |
| Logic | Vanilla JavaScript (no framework) |
| Chart | [Chart.js](https://www.chartjs.org/) via CDN |
| Storage | `localStorage` |
| Backend | None |

## Deployment

### GitHub Pages
1. Create a new repo (or use an existing one)
2. Drop `ai-career-tools-workshop.html` in the root (rename to `index.html` for a cleaner URL)
3. Settings → Pages → Source: main branch → Save
4. Live at `https://yourusername.github.io/repo-name/`

### Vercel
```bash
# From this folder
vercel deploy
```
Or drag-and-drop the file at vercel.com/new.

### Local
```bash
# Any of these work
open ai-career-tools-workshop.html          # macOS
python3 -m http.server 8080                 # then visit localhost:8080
npx serve .                                 # Node.js
```

## Customization

All data is defined at the top of the `<script>` block:

| Variable | What it controls |
|----------|-----------------|
| `FRAMEWORKS` | Competency keywords, suggestions, action verbs for NACE and KYCPE |
| `QUESTIONS` | Behavioral interview question list |
| `LI_SECTIONS` | LinkedIn checklist categories and items |

To add a new competency framework, add a new key to `FRAMEWORKS` with the same shape as `nace` or `kycpe`, then add an `<option>` to the `#framework-select` dropdown.

## File Structure

```
AI Career Tools/
├── ai-career-tools-workshop.html   # Complete self-contained app
└── README.md
```

## Disclaimer

This tool is for educational purposes. Students should always review and personalize AI-generated content. Developed by University of Louisville Libraries.
