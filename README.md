# London Weather Data — Resampling Datetime Data

A data analysis project using historical London weather data to practice datetime indexing, resampling, and visualization with pandas and matplotlib.

---

## Overview

This project loads daily weather data from London (sourced from Kaggle), cleans and prepares it for time-series analysis, then answers two questions about precipitation and temperature trends using resampled visualizations.

---

## Dataset

- **Source:** [Google Sheets (CSV export)](https://docs.google.com/spreadsheets/d/e/2PACX-1vT_jChgNsQbHbg4TGepzIqk8XC9DTIKmyyxb1upo5cfZCgbfIUQc2ZC0YMzuU5uApP140Ob49KBjdqh/pub?gid=1198589591&single=true&output=csv)
- **Date range used:** 2000 onwards
- **Features used:** `precipitation`, `mean_temp`, `min_temp`, `max_temp`, `snow_depth`

---

## Part 1: Data Preparation

- Converted the `date` column to `datetime` dtype and set it as the index
- Filtered to records from **2000 onward**
- Selected only the 5 required features
- Imputed missing values using feature-appropriate methods:

| Feature | Method | Reason |
|---|---|---|
| `precipitation` | `.bfill()` | Fill from next available record |
| `snow_depth` | `.bfill()` | Fill from next available record |
| `mean_temp`, `min_temp`, `max_temp` | `.interpolate()` | Temperature is continuous; interpolation gives the most realistic estimate |

---

## Part 2: Questions & Visualizations

### Q1 — What month had the most precipitation between 2000–2010?
- Resampled precipitation to **monthly frequency** using `.sum()`
- Plotted with major x-ticks every year and minor ticks every 3 months
- Marked the peak month with a vertical line and legend label

### Q2 — Which year between 2000–2020 had the coolest average temperature?
- Resampled mean temperature to **yearly frequency** using `.mean()`
- Plotted with major x-ticks every 5 years and minor ticks every year
- Marked the coldest year with a vertical line and legend label

---

## Dependencies

```
pandas
matplotlib
numpy
```

---

## How to Run

Open the notebook in [Google Colab](https://colab.research.google.com/) and run all cells in order. No local installation required.
