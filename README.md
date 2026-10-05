# AMR-ALERT

**AMR-ALERT (Antimicrobial Resistance Alert Framework)** is a surveillance-based framework for forecasting when antimicrobial resistance is expected to reach a predefined threshold.

The workflow was developed for national phenotypic antimicrobial-resistance surveillance data and is demonstrated using:

- **England:** UK Health Security Agency (UKHSA) Data Dashboard API data.
- **Japan:** Japan Nosocomial Infections Surveillance (JANIS) annual blood-isolate surveillance data.

The framework fits a log-odds resistance trend for each pathogen–antibiotic time series, estimates threshold-crossing time, quantifies uncertainty using residual bootstrap analysis, and classifies forecast reliability as **PASS**, **CAUTION**, or **FAIL**.

## Repository contents

- `AMR_ALERT_UK_JP_GitHub_final.ipynb` — main AMR-ALERT forecasting notebook for England and Japan.
- `janis_compact_blood_named_validated.csv` — processed aggregate JANIS blood-isolate surveillance dataset used by the notebook.

## Run the notebook

The notebook can be run in Google Colab or a compatible Jupyter environment.

1. Open `AMR_ALERT_UK_JP_GitHub_final.ipynb`.
2. Place `janis_compact_blood_named_validated.csv` in the same working directory as the notebook.
3. Run the notebook from the first cell onward.
4. Select the country, pathogen, antibiotic and resistance threshold using the notebook controls.

England analyses retrieve current surveillance data from the UKHSA Data Dashboard API. Therefore, England analyses require internet access and depend on the availability of the UKHSA API.

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
- PASS / CAUTION / FAIL forecast classification;
- single-series and batch analysis.

No patient-level data are included in this repository.

## Associated manuscript

**AMR-ALERT: Forecasting Phenotypic Antimicrobial Resistance Thresholds from National Surveillance Data**

The repository is intended to support reproducibility and practical implementation of the AMR-ALERT framework described in the manuscript.
