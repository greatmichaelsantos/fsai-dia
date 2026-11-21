# Data

Raw and processed data are **not committed**: the Phase 1 output alone is 181 MB, over GitHub's 100 MB file limit. Run `notebooks/01_phase1_preprocessing.ipynb` to download everything from source. The full URL list, with sizes and retrieval time, is in `outputs/phase1/data_inventory.csv`.

| Source | Access |
|---|---|
| Project NOAH hazard maps (flood 5/25/100-yr, storm surge SSA1–4), Zambales | https://huggingface.co/datasets/bettergovph/project-noah-hazard-maps |
| NASA POWER daily point API (PRECTOTCORR, T2M, RH2M), 1981-01-01 onward | https://power.larc.nasa.gov/api/temporal/daily/point |
| geoBoundaries gbOpen PHL ADM2/ADM3 | https://www.geoboundaries.org/api/current/gbOpen/PHL/ADM3/ |

Retrieved 2026-11-16 07:00 UTC.

## Integrity fingerprints (SHA-256, first 16 hex characters)

| File | Bytes | SHA-256 prefix |
|---|---|---|
| FSAI_DIA_Phase1_outputs.zip | 181,061,091 | d2ea32b17ce505a3 |
| clean/rainfall_daily_clean.csv | 38,944,512 | 42280664e30dab12 |
| clean/dia_hazard_by_lgu.gpkg | 206,635,008 | 003a23d87fa48cf5 |
| clean/lgu_features.csv | 2,442 | ebd80813a16d2b46 |
| outputs/phase2/lgu_features_corrected.csv | 8,833 | 3bf47edae586064a |
| outputs/phase2/model_artifacts.pkl | 60,803 | bfda471db1c060bb |
| outputs/phase2/experiment_log.csv | 25,126 | b82dc2dadbca2e4b |

Note that a fresh download may not reproduce the same hashes. POWER revises and extends its records, and the end date moves forward.
