# AI Career Tools Workshop Simulator — Claude Context

## What this project is

Single-file HTML app for University of Louisville Libraries. Used in library instruction sessions to teach students how to use AI responsibly in their job search. No backend, no build step, no dependencies except Chart.js via CDN.

**File:** `ai-career-tools-workshop.html` — everything lives here.

## Architecture

One HTML file with three sections:
1. `<style>` block — all CSS
2. `<body>` — header, tab nav, three tab panels, footer
3. `<script>` block — all JS

### Key data structures (top of `<script>`)
- `FRAMEWORKS` — object with keys `nace` and `kycpe`. Each has a `competencies` array where every item has: `name`, `keywords[]`, `suggestion`, `verbs[]`
- `QUESTIONS` — array of 15 behavioral interview question strings
- `LI_SECTIONS` — array of LinkedIn checklist sections, each with `title` and `items[]`

### localStorage keys
All prefixed `uofl_` to avoid collisions:
- `resume_text` — pasted resume
- `resume_fw` — selected framework (`nace` | `kycpe`)
- `active_tab` — last active tab (`resume` | `interview` | `linkedin`)
- `star_{index}` — object `{s,t,a,r}` per question index (0–14)
- `last_q` — last selected question index
- `li_checks` — object `{li_0: bool, li_1: bool, ...}` for all 20 checkboxes

## Branding rules

- Primary: Cardinal Red `#AD0000` (hover: `#8a0000`)
- Nav bar: Black `#000000`
- Body background: White `#FFFFFF`
- Card backgrounds: `#F5F5F5`, borders `#E0E0E0`
- Font: `'Helvetica Neue', Arial, sans-serif`
- Do NOT add other brand colors or frameworks (Bootstrap, Tailwind, etc.)

## How to make common changes

**Add a new interview question:**
Append to the `QUESTIONS` array. No other changes needed.

**Add a LinkedIn checklist item:**
Add the string to the correct `items[]` array inside `LI_SECTIONS`. The total item count drives the score denominator — it will update automatically. Update the "20 criteria" copy in the tab header if the count changes significantly.

**Add a new competency framework:**
1. Add a new key to `FRAMEWORKS` with the same shape as `nace`:
   ```js
   myfw: {
     name: 'Display Name',
     competencies: [{ name, keywords, suggestion, verbs }, ...]
   }
   ```
2. Add an `<option value="myfw">` to `#framework-select`

**Change keyword matching logic:**
See `makeVariants()` and `matchKeywords()` functions. Currently generates stemmed variants and tests with `\bword\b` regex, case-insensitive.

**Change score thresholds:**
In `analyzeResume()` for resume scoring; in `updateLiScore()` for LinkedIn scoring. Both use the same breakpoints: ≤40%/≤50% = red, ≤70%/≤75% = amber, else green.

## Deployment

No build step. Open the file directly or serve statically:
- GitHub Pages: rename to `index.html`, push to repo root
- Vercel: `vercel deploy` from this folder
- Local: `open ai-career-tools-workshop.html`

## What NOT to do

- Do not split into multiple files without a good reason — the single-file format is intentional for portability
- Do not add a backend or API calls — all processing is client-side by design
- Do not add npm/node dependencies — this must remain openable as a plain HTML file
- Do not change the UofL branding colors without explicit instruction
