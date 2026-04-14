# UNICEF Youth Out-of-School Report
## BAA1030 Assignment 2

---

## 📁 File Structure

```
unicef_report/
├── report.qmd               ← Main Quarto document (render this)
├── custom.css               ← Custom stylesheet (light blue theme)
├── unicef_indicator_2.csv   ← UNICEF out-of-school rate data
├── unicef_metadata.csv      ← World Bank development indicators
├── _quarto.yml              ← Quarto project config
└── README.md                ← This file
```

---

## 🚀 How to Render & Publish

### Step 1 — Upload to Google Colab

1. Open [Google Colab](https://colab.research.google.com)
2. Create a **new notebook**
3. Upload the entire `unicef_report/` folder contents to Colab, or mount Google Drive

### Step 2 — Install Dependencies in Colab

Run these cells in sequence:

```python
# Cell 1: Install system dependencies
!apt-get install -y quarto

# Cell 2: Install Python packages
!pip install polars plotnine pandas numpy
```

### Step 3 — Render the Report

```python
# Cell 3: Navigate to the report directory and render
import os
os.chdir('/content/unicef_report')   # adjust path if needed

!quarto render report.qmd --to html
```

This produces `report.html` (self-contained — no external files needed for sharing).

### Step 4 — Publish to GitHub Pages

Option A — **Quarto Publish** (recommended):
```bash
# From your local machine after cloning your DCU GitHub repo
quarto publish gh-pages report.qmd
```

Option B — **Manual upload**:
1. Create a GitHub repo with your DCU student email account
2. Enable **GitHub Pages** (Settings → Pages → Source: main branch, /root or /docs)
3. Upload `report.html` and rename to `index.html`
4. Your report will be live at `https://<username>.github.io/<repo-name>/`

---

## 📦 Python Package Versions Tested

| Package   | Version  |
|-----------|----------|
| polars    | ≥ 0.20   |
| plotnine  | ≥ 0.13   |
| pandas    | ≥ 2.0    |
| numpy     | ≥ 1.24   |

---

## 🎨 Theme Notes

- **Background:** White (`#ffffff`)
- **Heading colour:** Royal Blue (`#1a3a8c`)
- **Accent / links:** Medium blue (`#4a90d9`)
- **Panel backgrounds:** Light blue (`#e8f4fd`, `#f5faff`)
- **Base theme:** Quarto `flatly` + `custom.css` overrides

---

## ⚠️ Notes

- The `report.qmd` uses `embed-resources: true` — the rendered HTML is fully self-contained.
- All four required visualisations are present: world map, bar chart, scatterplot with regression, time-series.
- Charts are built exclusively with `plotnine`.
- Data manipulation uses `polars`.
- Hashpipe options (`#| label`, `#| fig-cap`, `#| code-summary`, `#| fig-width`, `#| fig-height`) are used throughout.
