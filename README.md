# DIA — Disaster Intelligence Atlas (FSAI, Inc.)

CSE315 Data Science final project. This repo applies the full CRISP-DM process to flood exposure and extreme-rain warning for **Zambales and Olongapo City** (14 LGUs). Everything is built from public government data, and every number can be regenerated from these notebooks.

| Phase | Notebook | What it does | Outputs |
|---|---|---|---|
| 1 · Business & Data Understanding | `notebooks/01_phase1_preprocessing.ipynb` | Downloads NOAH hazard maps, NASA POWER rainfall and geoBoundaries; EDA, cleaning, imputation, integration, transformation, reduction | `outputs/phase1/` (run summary, data dictionary, inventory, figures) |
| 2 · Modeling & Tuning | `notebooks/02_model_pipeline.ipynb` | Correlation, k-Means, association rules (mlxtend), network (networkx); logistic regression, LDA, decision tree, MLP, linear regression; H1–H4 | `outputs/phase2/` (experiment log, `model_artifacts.pkl`, figures) |
| 3 · Visualization Portfolio | `notebooks/03_visualization_portfolio.ipynb` | Portfolio figures V01–V15: ROC curves, confusion matrices, event replay, executive dashboard | `outputs/portfolio/` |

## Headline results
- **Exposure growth:** high-hazard flood land rises from 3.3% to 10.4% (median) between the 5-year and 100-year events, across the 10 jointly mapped LGUs. Wilcoxon p = 0.001.
- **Three stable exposure clusters** (k-Means, bootstrap ARI 0.83). The coastal double-exposure cluster is Iba, San Felipe and San Narciso.
- **Rising extremes:** the wettest day of the year is up 14–17 mm per decade since 1981 (Mann–Kendall p ≤ 0.005).
- **Next-day extreme-rain classifier** (logistic regression) on the 2021–2026 hold-out: ROC-AUC 0.917, recall 0.51, precision 0.41.

## Reproduce
1. Open `01_phase1_preprocessing.ipynb` in Google Colab and choose *Run all*. It takes about 30–45 minutes and downloads `FSAI_DIA_Phase1_outputs.zip`.
2. Put that zip next to `02_model_pipeline.ipynb` and *Run all* (about 12 minutes). This produces `FSAI_DIA_Phase2_outputs.zip`.
3. Put both zips next to `03_visualization_portfolio.ipynb` and *Run all* (about 1 minute).

Seeds are fixed (42), so reruns reproduce the logged metrics. Raw data is not committed: see `data/README.md` for sources and SHA-256 fingerprints.

## Data sources and licenses
- Project NOAH hazard maps, via the BetterGov.PH Hugging Face mirror (ODbL)
- NASA POWER daily point data (NASA Langley Research Center)
- geoBoundaries gbOpen PHL ADM2/ADM3 (CC BY 3.0 IGO)

## Limitations
- Not real-time: NOAH maps are static, and POWER lags by several days.
- No observed flood records, so the model predicts extreme rain, not inundation.
- The NOAH 5- and 25-year maps do not cover Candelaria, Masinloc, Palauig or Santa Cruz.
- LGU-level classifiers (n = 14) performed at chance and are reported as negative results.


Full details are in the Final Technical & Forensic Report.
