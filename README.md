# Three Rivers Analytics — Pittsburgh's Best Neighborhood

> **One-sentence overview:** This repository is a data-driven investigation, using four WPRDC datasets, that identifies the "best" Pittsburgh neighborhood by combining three independently computed sub-metrics — green space, safety, and cultural vibrancy — into a single composite score.

## Team

**Team name:** Three Rivers Analytics  
**Canvas group:** _Final Project Group — **TODO: fill in your Canvas group number before submitting**_

| Team member | Email | Individual notebook(s) |
|-------------|-------|------------------------|
| Sohan Udumula | sudumula8@gmail.com | `sohan_greenspace.ipynb` (Green Space) and `sohan_safety.ipynb` (Safety) |
| Pranav | prj58@pitt.edu | `pranav.ipynb` (Cultural Vibrancy) |
| Aayan | aab430@pitt.edu | `aayan.ipynb` / `final_report.ipynb` (Combined analysis & final report) |

Each member's individual notebook shows *that member's own work* — their dataset(s), analysis, and conclusion. The combined notebook (`final_report.ipynb`, also available as `aayan.ipynb`) merges all three sub-metrics into the team's final answer, with a reflection paragraph from every team member.

## Repository Structure

```
├── final_report.ipynb           # Combined team notebook & presentation notebook
├── aayan.ipynb                  # Aayan's individual notebook (same content — he owns the combining work)
├── sohan_greenspace.ipynb       # Sohan's individual: Green Space sub-metric
├── sohan_safety.ipynb           # Sohan's individual: Safety sub-metric
├── pranav.ipynb                 # Pranav's individual: Cultural Vibrancy sub-metric
└── README.md                    # This file
```

Our team chose to analyze four datasets (more than the three-dataset minimum). Sohan took on two sub-metrics (green space + safety), Pranav took cultural vibrancy, and Aayan owned the integration / final report.

## Our Metric

We define the "best neighborhood" as the one with the highest **composite score**, computed as an equal-weighted average of three sub-scores:

- 🌳 **Green Score** — `0.6 × norm(tree_count) + 0.4 × norm(env_benefit)` (from the trees dataset)
- 🔒 **Safety Score** — `1 − norm(incident_count)` (from the police-blotter dataset)
- 🎨 **Vibrancy Score** — `0.5 × norm(park_count) + 0.5 × norm(art_count)` (from the parks + public-art datasets)

All sub-scores are normalized to `[0, 1]` before combining:

```
Best Score = (Green + Safety + Vibrancy) / 3
```

## Datasets Used

All data is from the [Western Pennsylvania Regional Data Center (WPRDC)](https://data.wprdc.org), Pittsburgh's open data portal.

| Dataset | Source | Records | Used in | Link |
|---------|--------|---------|---------|------|
| City of Pittsburgh Trees | WPRDC | ~45,709 | `sohan_greenspace.ipynb` | https://data.wprdc.org/dataset/city-trees |
| Police Incident Blotter (Archived) | WPRDC | 50,000-row sample | `sohan_safety.ipynb` | https://data.wprdc.org/dataset/uniform-crime-reporting-data |
| City of Pittsburgh Parks | WPRDC | 209 | `pranav.ipynb` | https://data.wprdc.org/dataset/parks |
| City of Pittsburgh Public Art | WPRDC | 199 | `pranav.ipynb` | https://data.wprdc.org/dataset/city-of-pittsburgh-public-art |

All four datasets are also used in `final_report.ipynb` / `aayan.ipynb` to compute the combined composite score.

## Result

🏆 **Pittsburgh's Best Neighborhood: Squirrel Hill South** (composite score **0.776**)

Runner-up: Central Business District (0.650). Third: Highland Park (0.535).

Squirrel Hill South wins because it is the only neighborhood that ranks well across *all three* dimensions — it has the most city-maintained trees of any Pittsburgh neighborhood (5,073), a below-average crime rate despite its large size, and strong parks + public-art presence. It's a balanced winner, not a one-dimensional one.

## How to Run

Each notebook pulls data live from the WPRDC API (no static CSVs are stored in the repo). To reproduce:

1. Clone the repo and `cd` into it.
2. Create a Python environment with `pandas`, `numpy`, `matplotlib`, and `requests` installed.
3. Open any notebook in Jupyter and run all cells top to bottom.

Expect `final_report.ipynb` to take ~1–2 minutes to fetch all four datasets the first time.
