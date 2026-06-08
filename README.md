# GeoPulse Intelligence — Commodities & Currency Markets (DSB)

Data-analytics study of long-run **commodity prices** (Brent Oil, Gold, Silver) and **global currency-payment indicators** (SWIFT tracker), produced for the *Applied Data Analytics and Market Research* assignment. The work takes the perspective of a junior market analyst: clean the data, describe and visualise it, and surface findings a non-technical manager can act on.

This repository covers **Part I — the Data Analytics Component**: data preparation, descriptive statistics, trend/visual analytics, currency-tracker analysis and simple comparisons (30 questions in total).

---

## Datasets

| Dataset | File | Period | Rows | Description |
|---|---|---|---|---|
| Brent Oil | `data/Brent_Oil.csv` | Jan 1946 – Mar 2026 | 963 | Monthly Brent crude price (USD/barrel) |
| Gold | `data/Gold_100years.csv` | Jan 1915 – Apr 2026 | 1,336 | Monthly gold price (USD/ounce) |
| Silver | `data/silver_100_years.csv` | Jan 1915 – Apr 2026 | 1,336 | Monthly silver price (USD/ounce) |
| SWIFT Currency Tracker | `data/swift_currency_tracker_all_reports.csv` | Reports Jan – Apr 2026 | 330 | Currency payment shares, rankings, offshore RMB activity (long/tidy format) |

All four files are clean — no missing values and no duplicate dates. Commodity series are monthly observations dated to the first of each month. Values for early 2026 are taken exactly as supplied and treated as the latest available data.

---

## Repository structure

```
Geopulse-Intelligence-DSB/
├── README.md                     # this file
├── requirements.txt              # Python dependencies
├── .gitignore
├── data/                         # raw input datasets
│   ├── Brent_Oil.csv
│   ├── Gold_100years.csv
│   ├── silver_100_years.csv
│   └── swift_currency_tracker_all_reports.csv
├── DSB_Part1_Analysis.ipynb      # notebook: all figures & tables
└── DSB_Cleaned_Datasets.xlsx     # cleaned, preprocessed workbook (5 sheets)
```

> The notebook reads its inputs from the `data/` folder (`DATA_DIR = 'data'`). If you keep the CSVs somewhere else, update that one line at the top of the setup cell.

---

## Getting started

```bash
# 1. Clone
git clone https://github.com/Koushiksunny44/Geopulse-Intelligence-DSB.git
cd Geopulse-Intelligence-DSB

# 2. (Optional) create a virtual environment
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Launch the notebook
jupyter notebook DSB_Part1_Analysis.ipynb
```

Run the cells top to bottom. The notebook is organised question-by-question; each figure and table is preceded by a header naming it (e.g. *Figure 1 · Q13*, *Table 5 · Q10–Q12*).

---

## What the notebook produces

**7 figures**

1. Brent Oil price over time (1946–2026)
2. Gold price over time (1915–2026)
3. Silver price over time (1915–2026)
4. Gold vs Silver — dual-axis comparison
5. Average annual Brent Oil price, last 10 years
6. Top 10 currencies by global payment share (latest month)
7. Summary dashboard (4-panel)

**12 tables** — dataset coverage & quality, SWIFT metrics, high/low prices, annual averages, top-five years, latest values, currency rankings, top-five frequency, latest-vs-average comparisons, volatility, and a crisis-year comparison.

To export the charts as PNGs, uncomment the `fig.savefig(...)` line under Figure 1 (and add similar lines elsewhere).

---

## Cleaned data workbook

`DSB_Cleaned_Datasets.xlsx` contains the preprocessed data used for the analysis, across five sheets:

- **Cleaning_Notes** — documentation of every preprocessing step
- **Brent_Oil_clean / Gold_clean / Silver_clean** — parsed `Date`, `Value`, plus live `=MONTH()` / `=YEAR()` formula columns
- **SWIFT_clean** — all 330 records with an added parsed `Data Month Date` column

---

## Selected findings

- **Precious metals at record highs.** Gold and silver climb to all-time peaks in 2025–2026, the steepest move in their century-long series.
- **Oil is the most event-sensitive commodity.** Brent shows the largest month-to-month volatility (≈9%), with repeated event-driven spikes and collapses.
- **The US Dollar dominates global payments** at ~51% (March 2026); the Chinese Renminbi ranks 5th at ~3%, and offshore RMB activity is concentrated in Hong Kong (~75%).

---

## Tech stack

Python · pandas · NumPy · Matplotlib · openpyxl · Jupyter

## Notes & licence

- Confirm you have the right to redistribute the bundled datasets before making the repository public.
- Add a `LICENSE` file if you intend others to reuse the code (e.g. MIT for the analysis code).
