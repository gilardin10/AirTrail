# ✈ AirTrail

A personal flight tracker that reads live from a Google Sheet and visualises your travel history on an interactive map with stats, charts, and filters.

## Features

- **Interactive map** with curved flight routes coloured by trip type
- **Stats bar** — total flights, km flown, time in air, longest flight, countries visited, unique trips — all reactive to active filters
- **Filters** — by year, trip type, and who was travelling (Gil / Magda / Noa)
- **Charts** — flights per year, distance per year, top destinations, trip type breakdown
- **Flight log table** — sortable, with traveller badges per row
- **No backend** — pure HTML/JS, hosted on GitHub Pages
- **Privacy** — sheet ID is never hardcoded; entered once by the user and stored in the browser (`localStorage`)

## Setup

### 1. Prepare your Google Sheet

The sheet must have these columns in row 1 (exact names, case-insensitive):

| Column | Description | Example |
|---|---|---|
| `Date` | Year, year-month, or full date | `2026`, `2026-03`, `2026-03-24` |
| `From` | Departure city | `Porto` |
| `To` | Arrival city | `Warsaw` |
| `Reason` | Trip name (used for type classification) | `2026 Japan` |
| `Distance` | Distance in km (optional) | `2500 km` or `2500` |
| `Time` | Flight duration in decimal hours (optional) | `3.5 h` |
| `Gil` | Checkbox — was Gil on this flight? | `TRUE` / `FALSE` |
| `Magda` | Checkbox — was Magda on this flight? | `TRUE` / `FALSE` |
| `Noa` | Checkbox — was Noa on this flight? | `TRUE` / `FALSE` |

Use **Insert → Checkbox** in Google Sheets for the Gil/Magda/Noa columns.

### 2. Share the sheet

**File → Share → Share with others → Anyone with the link → Viewer**

### 3. Open the app

Go to your hosted URL (e.g. `https://gilardin10.github.io/AirTrail`).

On first visit a setup screen appears. Paste the full Google Sheets URL — the app parses the sheet ID and tab ID automatically and stores them locally.

To switch sheets later, click **⚙ Change sheet** in the header.

## Trip type classification

The `Reason` field is matched against keywords to assign a type:

| Type | Keywords matched |
|---|---|
| Business | `business` |
| Visit Home | `home`, `christmas at`, `nye at home` |
| Social | `birthday`, `wedding`, `parents` |
| Holiday | everything else |
| Other | empty reason |

## Deployment (GitHub Pages)

1. Push this repo to GitHub
2. Go to **Settings → Pages → Source: `master` / `(root)`**
3. Your site will be live at `https://<username>.github.io/AirTrail`

## Local development

No build step needed — open `index.html` directly in a browser.

> Note: fetching from Google Sheets requires an internet connection and a CORS-friendly browser. Most modern browsers work fine when opened from a file.
