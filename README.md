# Deep Learning-Based Prediction of Short-Term CO2 Emissions in Ireland

This repository contains the research notebook associated with the paper
**“Deep Learning-Based Prediction of Short-Term CO2 Emissions in Ireland,”**
published at the **2024 17th International Congress on Image and Signal
Processing, BioMedical Engineering and Informatics (CISP-BMEI)**.

**DOI:** [10.1109/CISP-BMEI64163.2024.10906112](https://doi.org/10.1109/CISP-BMEI64163.2024.10906112)

> **Terminology note:** Although the published title uses the term
> “emissions,” the implemented prediction target is atmospheric CO2
> concentration measured in parts per million (ppm) at Mace Head. It is not a
> mass-based emissions inventory.

## Publication

- **Authors:** Yiteng Zhang, Arjun Pakrashi, and Soumyabrata Dev
- **Conference:** 2024 17th International Congress on Image and Signal
  Processing, BioMedical Engineering and Informatics (CISP-BMEI)
- **Year:** 2024
- **DOI:** [10.1109/CISP-BMEI64163.2024.10906112](https://doi.org/10.1109/CISP-BMEI64163.2024.10906112)

Citation metadata are provided in [`CITATION.cff`](CITATION.cff).

## Repository contents

- [`co2.ipynb`](co2.ipynb) — the original exploratory analysis and modelling
  notebook associated with the paper.
- [`DATA.md`](DATA.md) — data provenance, citation, and local setup guidance.
- [`requirements.txt`](requirements.txt) — direct Python dependencies used by
  the notebook.

## Dataset

The notebook uses atmospheric CO2 surface-flask event measurements from the
NOAA Global Monitoring Laboratory.

| Field | Value |
|---|---|
| Provider | NOAA Global Monitoring Laboratory |
| Site | Mace Head, County Galway, Ireland |
| Site code | `MHD` |
| Product | Surface-flask event CO2 data |
| Parameter | Atmospheric CO2 dry-air mole fraction (ppm) |
| Paper period | 1991-06-03 to 2022-12-22 |
| Expected filename | `co2_mhd_surface-flask_1_ccgg_event.txt` |
| Expected local path | `IRE_GHG/co2_mhd_surface-flask_1_ccgg_event.txt` |

The raw NOAA file is **not distributed in this repository**. Obtain it from
NOAA and place it at the expected local path before using the notebook. The
`IRE_GHG/` directory is excluded by `.gitignore` to prevent accidental data
commits. See [`DATA.md`](DATA.md) for details.

## Methods represented in the notebook

The notebook implements an exploratory univariate CO2 forecasting workflow:

1. IQR-based outlier detection and neighbour-mean replacement.
2. Conversion of flask-event observations to a daily series.
3. Linear interpolation of missing daily values.
4. MinMax scaling for the LSTM experiments.
5. Ten-step input windows for short-term forecasting.
6. A two-layer LSTM model.
7. A regularized LSTM using Dropout and Early Stopping.
8. Random Forest and Decision Tree comparison models.
9. Exploratory Bidirectional LSTM (BiLSTM) code.

The **published comparison models** are LSTM, Random Forest, and Decision Tree.
BiLSTM was described as future work in the paper; its notebook cells should be
understood as an exploratory extension rather than part of the published model
comparison.

## Published results

The following MSE values are **Table I results reported in the published
paper**. They are presented for reference and are not claimed here as newly or
independently reproduced results.

| Forecast horizon (days) | LSTM | Random Forest | Decision Tree |
|---:|---:|---:|---:|
| 1 | 21.2579 | 7.1929 | 16.4430 |
| 2 | 39.8614 | 15.1050 | 28.1521 |
| 3 | 51.7581 | 27.3721 | 41.7251 |
| 4 | 51.3234 | 43.2375 | 58.5974 |
| 5 | 53.9563 | 61.9931 | 77.7077 |
| 6 | 58.1840 | 82.4240 | 95.5688 |
| 7 | 33.2322 | 103.0139 | 109.2281 |

## Setup

1. Clone the repository and enter its directory.

   ```bash
   git clone https://github.com/Yiteng369/GHG-Ireland.git
   cd GHG-Ireland
   ```

2. Create and activate a virtual environment.

   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```

   On Windows, activate it with:

   ```powershell
   .venv\Scripts\Activate.ps1
   ```

3. Install the notebook dependencies.

   ```bash
   python -m pip install -r requirements.txt
   ```

4. Obtain the NOAA data and place it at:

   ```text
   IRE_GHG/co2_mhd_surface-flask_1_ccgg_event.txt
   ```

5. Start Jupyter from the repository root and open `co2.ipynb`.

   ```bash
   jupyter notebook co2.ipynb
   ```

The notebook is stateful and should be read or run in cell order.

## Limitations

- The notebook represents the original exploratory research workflow.
- The raw data are not included.
- Exact historical package versions were not preserved.
- Some preprocessing choices should be interpreted as part of the original
  study design.
- The repository has not been reorganized into a production software package.
