# Data

This directory contains the datasets used and generated during the project.

## Source Data

`raw_data.csv` contains the consolidated source data obtained from the official Greek Real Estate Transactions Valuation Register (Μητρώο Αξιών Μεταβιβάσεων Ακινήτων).

Annual datasets covering 2017–2026 were manually downloaded from the public register and consolidated into a single dataset for analysis.

The source variables are retained in their original form in `raw_data.csv`.

## Derived Datasets

* `cleaned_data.csv` — cleaned and transformed dataset produced during the data-preparation stage.
* `cleaned_data.parquet` — Parquet version of the cleaned dataset.
* `modeling_data.parquet` — subset of the cleaned data containing the variables selected for the planned transaction-price modelling task.

## Data Processing

The transformation from the raw source data to the analytical datasets is documented in:

`notebooks/01_data_preparation.ipynb`

The subsequent exploratory analysis is documented in:

`notebooks/02_descriptive_analysis.ipynb`

The project uses these files to maintain a clear distinction between the original source data and the derived analytical datasets.