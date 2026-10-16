# AMR-ALERT

**AMR-ALERT (Antimicrobial Resistance Alert Framework)** is a surveillance-based framework for forecasting when antimicrobial resistance is expected to reach a predefined threshold.

The workflow was developed for national phenotypic antimicrobial-resistance surveillance data and is demonstrated using:

- **England:** UK Health Security Agency (UKHSA) Data Dashboard API data.
- **Japan:** Japan Nosocomial Infections Surveillance (JANIS) annual blood-isolate surveillance data.

The framework fits a log-odds resistance trend for each pathogen–antibiotic time series, estimates threshold-crossing time, quantifies uncertainty using residual bootstrap analysis, and assigns **OBSERVED ALERT** when the latest resistance is already at or above the selected threshold; otherwise prospective results are classified as **PASS**, **CAUTION**, or **FAIL** using model-based suitability criteria (not demonstrated forecast accuracy).

## Repository contents

- `AMR_ALERT_UK_JP_GitHub_final.ipynb` — AMR-ALERT forecasting notebook for England and Japan, including residual diagnostics (Cell 5).
- `janis_compact_blood_named_validated.csv` — processed aggregate JANIS blood-isolate surveillance dataset used by the notebook.
- `README.md` — implementation instructions and data provenance.
- `LICENSE` — MIT license for software code (not the JANIS-derived dataset).

## Run the notebook

The notebook can be run in Google Colab or a compatible Jupyter environment.

1. Open `AMR_ALERT_UK_JP_GitHub_final.ipynb`.
2. Place `janis_compact_blood_named_validated.csv` in the same working directory as the notebook.
3. Run the notebook from the first cell onward.
4. Select the country, pathogen, antibiotic and resistance threshold using the notebook controls.
5. For the residual diagnostic assessment, run Cell 5 after Cells 1–3. Cell 5 exports `AMR_ALERT_Residual_Diagnostics_All.csv`; it does not change the forecasting calculations or classifications.

England analyses retrieve surveillance data from the UKHSA Data Dashboard API. UKHSA monthly resistance values are three-month rolling averages. The API may be updated over time, so results from later runs may differ from the historical manuscript outputs. England analyses require internet access.

Japan analyses use the included processed JANIS dataset.

## AMR-ALERT calculator

A browser-based implementation of AMR-ALERT is available at:

https://ais-pre-cdexfhuhijsgno5pycqwy6-307319855103.europe-west3.run.app/

The calculator provides an interactive implementation of the same AMR-ALERT forecasting framework.

## Data sources

### UKHSA

England surveillance data are obtained from the UK Health Security Agency Data Dashboard API. The notebook retrieves the relevant public surveillance time series directly from UKHSA.

UKHSA Data Dashboard:

https://ukhsa-dashboard.data.gov.uk/

### JANIS

Japan surveillance data are derived from publicly available **Japan Nosocomial Infections Surveillance (JANIS)** Clinical Laboratory Division Open Reports and are restricted to blood isolates.

JANIS:

https://janis.mhlw.go.jp/english/

`janis_compact_blood_named_validated.csv` is a processed aggregate dataset prepared for the AMR-ALERT analysis. It is not an original dataset produced or endorsed by JANIS.

## Reproducibility

The main notebook contains the complete AMR-ALERT forecasting workflow used for the England and Japan analyses, including:

- surveillance-data loading and validation;
- log-odds transformation and linear regression;
- threshold-crossing estimation;
- residual-bootstrap uncertainty assessment;
- OBSERVED ALERT and prospective PASS / CAUTION / FAIL classification;
- single-series and batch analysis;
- residual diagnostic tests (lag-1 Ljung–Box, Breusch–Pagan, and Shapiro–Wilk) and CSV export.

No patient-level data are included in this repository.

## Computational environment

Run in **Google Colab** or a compatible **Python/Jupyter** environment. The notebook uses `numpy`, `pandas`, `matplotlib`, `ipywidgets`, `requests`, `openpyxl`, `scipy`, and `statsmodels`. Exact package versions and operating-system versions are not pinned here.

## Associated manuscript

**Antimicrobial Resistance Alert Framework: Forecasting Resistance Thresholds from National Surveillance Data**

The repository is intended to support reproducibility and practical implementation of the AMR-ALERT framework described in the manuscript.

## License

The AMR-ALERT software and notebook code in this repository are released under the MIT License.

The file `janis_compact_blood_named_validated.csv` is a processed aggregate dataset derived from publicly available JANIS surveillance reports. It is included for reproducibility and is **not relicensed under the MIT License**. Use of JANIS-derived data should retain appropriate JANIS source attribution and follow the applicable JANIS terms of use.

UKHSA surveillance data are retrieved from the UKHSA Data Dashboard API and are not redistributed as a separate dataset in this repository.
