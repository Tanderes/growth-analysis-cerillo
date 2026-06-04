# growth-analysis-cerillo

A standalone, browser-based growth curve analysis tool for 96-well and 384-well plate reader data. No installation, no server, no cost — just open `index.html`.

---

## Live App

🔗 **[Open the app](https://tanderes.github.io/growth-analysis-cerillo/)**

---

## Features

- **96-well and 384-well plate support**
- **CSV and Excel upload** (.csv, .xls, .xlsx) — compatible with Welly plate reader exports
- **Plate map assignment** — upload a plate map CSV or fill in the well grid manually
- **Interactive charts** (Plotly)
  - Optical density over time (mean ± std, per sample)
  - Max growth rate bar chart (OD/hr)
  - Area under the curve bar chart (OD·h)
  - Plate heatmap of maximum OD values
- **Double-click legend** to isolate a single strain trace
- **Per-sample colour pickers** with randomise option
- **Exports**
  - HTML report (all charts + summary table)
  - Summary CSV (growth rate + AUC per sample)
  - PNG download for each bar chart
- **Template downloads** built into the app (absorbance + layout map)

---

## Quick Start

```
1. Go to https://tanderes.github.io/growth-analysis-cerillo/
   — or — download index.html and open it in any modern browser
2. Upload your plate reader CSV or Excel file
3. Upload or fill in a plate map
4. Explore and export results
```

No Python, no Node, no dependencies to install. All libraries load from CDN.

---

## Input File Formats

### Plate reader data

| Column | Description |
|--------|-------------|
| `Time` / `Duration (Hours)` / `Duration (Minutes)` | Time column (auto-detected) |
| `A1` … `H12` (96-well) or `A1` … `P24` (384-well) | OD readings per well |

Expected columns: **97** for 96-well, **385** for 384-well (time + wells).

### Plate map CSV

Rows = plate rows (A–H or A–P), columns = plate columns (1–12 or 1–24). Cell values = sample names. Wells with the same name are grouped as replicates.

```
,1,2,3,4,...
A,SampleA + c1,SampleB + c1,SampleC + c1,Control,...
B,SampleA + c1,SampleB + c1,SampleC + c1,Control,...
C,SampleA + c2,SampleB + c2,SampleC + c2,Control,...
```

Template files are available in [`example_data/`](example_data/) and as in-app downloads.

---

## Repository Structure

```
growth-analysis-cerillo/
├── index.html                             # The entire app — open this
├── example_data/
│   ├── growth_absorbance_template.csv     # 96-well plate reader template
│   └── growth_layout_template.csv        # Corresponding plate map template
├── LICENSE
└── README.md
```

---

## Deploying with GitHub Pages

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Source: **Deploy from a branch → main / root**
4. Your app will be live at `https://YOUR-USERNAME.github.io/growth-analysis-cerillo/`

---

## Credits & License

This project is a client-side HTML reimplementation of **[Welly](https://github.com/SynBioExplorer/Welly)** by Felix Meier, Tom Williams, and Ian Paulsen (Macquarie University / ARC Centre of Excellence in Synthetic Biology). The original analysis logic — max growth rate, AUC calculation, replicate grouping, and plate heatmap — is derived from their work.

If you use this tool in research, please cite the original paper:

> Felix Meier, Tom Williams, Ian Paulsen, **Welly: A Web-Tool for Visualizing Growth Curves from Microplate Data**, *Bioinformatics Advances*, 2025, vbaf038. https://doi.org/10.1093/bioadv/vbaf038

This repository is distributed under the MIT License. See [LICENSE](LICENSE) for the full text, including the original copyright notice.

---

## Dependencies (loaded via CDN)

| Library | Purpose |
|---------|---------|
| [Plotly.js](https://plotly.com/javascript/) | Interactive charts |
| [PapaParse](https://www.papaparse.com/) | CSV parsing |
| [SheetJS](https://sheetjs.com/) | Excel file reading |
