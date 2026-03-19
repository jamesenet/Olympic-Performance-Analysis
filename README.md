# Olympic Performance Analysis — What Actually Predicts Medal Counts?
**Exploratory Data Analysis | Python · Pandas · Seaborn**

[![Python](https://img.shields.io/badge/Python-3.10-blue?style=flat-square)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-EDA-green?style=flat-square)](https://pandas.pydata.org)
[![Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square)](https://jupyter.org)

---

## 1. Business Problem

A sports analytics brief posed the question every national Olympic committee asks:

> *"Beyond just having a large population, which country-level factors actually explain Olympic success — and which sports offer the best return on investment for a mid-tier sporting nation?"*

This matters for resource allocation: a country with a limited sports development budget needs to know whether to invest broadly or concentrate resources on specific disciplines with the highest medal conversion probability.

---

## 2. Data

| Source | Description | Coverage |
|--------|-------------|----------|
| Olympic results dataset | Medal counts by country, sport, year | 1976–2016 Summer Games |
| World Bank indicators | GDP, GDP per capita, population by country/year | Matched by year |
| NOC country codes | Country name standardisation | All participating nations |

**Data preparation steps:**
- Merged Olympic results with World Bank GDP data on country ISO code + year
- Handled dissolved/renamed nations (Soviet Union, East Germany, Yugoslavia) — flagged separately rather than dropped
- Normalised medal counts to **medals per million population** for fair cross-country comparison
- Created GDP per capita quintile bands for group-level analysis

---

## 3. Approach

```
Olympic results + World Bank GDP data
        ↓
Data merging & cleaning (Pandas)
        ↓
Feature creation (medals per capita, GDP quintile bands, sport concentration index)
        ↓
Correlation analysis — GDP vs medal counts (Pearson, Spearman)
        ↓
Sport-level analysis — Gini coefficient of nation distribution per sport
        ↓
Visualisation — Seaborn heatmaps, scatter plots, bar charts
        ↓
Insight synthesis & recommendations
```

---

## 4. Key Findings

### Finding 1 — GDP per capita beats population as a predictor
Countries in the top GDP per capita quintile won **3× more medals per capita** than equivalent-population countries in the bottom quintile. Raw population size alone has near-zero correlation with per-capita medal performance (r = 0.04).

### Finding 2 — Athletics & swimming dominate medal opportunity
Athletics and swimming together account for **38% of all available medals** at a Summer Games. For a country with limited resources, these two disciplines offer the highest total addressable medal count.

### Finding 3 — High-inequality sports are harder to break into
Sports with the highest Gini coefficient (i.e. medals concentrated in 2–3 nations) include: weightlifting super-heavy categories, artistic gymnastics, and canoe slalom. Mid-tier nations consistently fail to medal in these disciplines regardless of investment level.

### Finding 4 — The "small nation specialist" pattern
Nations with population < 5 million can achieve disproportionate medal hauls by concentrating entirely on 1–3 high-ceiling sports (e.g. Kenya: distance running; Jamaica: sprinting; Cuba: boxing). This concentration strategy is detectable in the data as a low sport-diversity index combined with high per-capita medal count.

---

## 5. Recommendations

| For | Recommendation |
|-----|---------------|
| Mid-budget NOCs | Prioritise athletics (track/field) and swimming — highest medal ceiling with distributed competition |
| Small-nation NOCs | Adopt the specialist model: identify 1–2 sports where the nation has cultural/geographic advantage and concentrate funding |
| Policy analysts | Use GDP per capita as the primary benchmark when comparing national Olympic "efficiency" — raw medal tables are misleading |

---

## 6. Files in This Repository

```
├── Olympics Dataset.ipynb     # Full EDA notebook
├── data/
│   ├── olympic_results.csv    # Cleaned medal data
│   └── world_bank_gdp.csv     # GDP indicators
└── README.md
```

---

## 7. Tools & Libraries

| Tool | Use |
|------|-----|
| Pandas / NumPy | Data merging, cleaning, aggregation |
| Seaborn | Heatmaps, scatter plots, distribution charts |
| Matplotlib | Custom figure layouts and annotations |
| SciPy | Correlation tests (Pearson, Spearman) |

---

## 8. How to Run

```bash
# Clone the repository
git clone https://github.com/jamesenet/Data-Science-

# Install dependencies
pip install pandas numpy matplotlib seaborn scipy

# Launch notebook
jupyter notebook "Olympics Dataset.ipynb"
```

---

*Case study by Cornelius Enetomhe · [LinkedIn](https://www.linkedin.com/in/cornelius-enetomhe-01688a266/) · [Portfolio](https://jamesenet.github.io/CorneliusEnetomhe.github.io/)*
