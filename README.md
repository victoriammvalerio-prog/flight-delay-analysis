# flight-delay-analysis
Analysis of 3M US domestic flights (2019–2023) using Python, pandas, and seaborn. Covers data cleaning, missing value investigation, and visualisation of delay patterns by airline, airport, cause, day of week, and month. Finds r=0.965 between departure and arrival delay.

## Dataset
[Flight Delay and Cancellation Dataset 2019–2023](https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023) — sourced from the US Bureau of Transportation Statistics (BTS).

- 3,000,000 flights
- 18 airlines
- 380 airports
- January 2019 – August 2023

## Key Findings

| Question | Finding |
|---|---|
| Worst airline (magnitude) | Allegiant Air — 13.4 min avg arrival delay |
| Worst airline (frequency) | JetBlue — 27% of flights delayed 15+ min |
| Best airline | Endeavor Air — only airline arriving early on average |
| Main delay cause | Late Aircraft (37.7%) + Carrier (36.7%) = 74% of all delay |
| Worst month to fly | June — 11.0 min avg delay |
| Best month to fly | September — 0.8 min avg delay |
| Worst day to fly | Friday — 6.7 min avg delay |
| Best day to fly | Tuesday — 2.7 min avg delay |
| Dep → Arr delay | r = 0.965; airlines recover ~6 min on average in the air |

## Analysis Structure

| Section | Content |
|---|---|
| 0 · Setup | Imports, constants, chart styling |
| 1 · Data Loading | Download from Kaggle, load single CSV |
| 2 · Data Cleaning | Missing value investigation, logical consistency checks, derived features |
| 3 · Analysis | 6 questions |

## Data Cleaning Decisions

A key finding during cleaning informed the entire analysis:

- **Delay cause columns** are only populated by the BTS when `ARR_DELAY >= 15 min` — this is the official reporting threshold, not a data quality issue
- **62,056 flights** depart on time but arrive late due to NAS/ATC congestion in the air — departure delay alone is not a reliable "delayed" flag
- **Canonical delay definition** used throughout: `ARR_DELAY >= 15 min`
- **2020 excluded** from seasonal analysis — COVID-19 caused ~37% fewer flights vs 2019
- **2023 is a partial year** (January–August only) — excluded from annual comparisons

## Setup

### Requirements
pandas
numpy
matplotlib
seaborn
jupyter

### Installation
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Data
Download the dataset from [Kaggle](https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023) and place the CSV in `data/raw/`. The data folder is excluded from this repository (too large to host, Kaggle license does not permit redistribution).

### Run
```bash
jupyter notebook flight_delay_analysis.ipynb
```

## Tools
Python · pandas · NumPy · Matplotlib · Seaborn · Jupyter
