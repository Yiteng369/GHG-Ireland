# Data documentation

## Dataset overview

The research notebook uses atmospheric carbon dioxide measurements from the
NOAA Global Monitoring Laboratory (GML) Global Greenhouse Gas Reference
Network.

| Field | Value |
|---|---|
| Provider | NOAA Global Monitoring Laboratory |
| Site | Mace Head, County Galway, Ireland |
| Site code | `MHD` |
| Coordinates | 53.326° N, 9.899° W |
| Nominal elevation | 5 m above sea level |
| Product | Carbon Cycle Cooperative Global Air Sampling Network, surface-flask event data |
| Parameter | Atmospheric CO2 dry-air mole fraction |
| Units | µmol mol⁻¹, conventionally reported as ppm |
| Calibration scale in the recovered file | `CO2_X2019` |
| Paper period | 1991-06-03 through 2022-12-22 |
| Expected filename | `co2_mhd_surface-flask_1_ccgg_event.txt` |
| Expected local path | `IRE_GHG/co2_mhd_surface-flask_1_ccgg_event.txt` |
| Product DOI | [10.15138/wkgj-f215](https://doi.org/10.15138/wkgj-f215) |

The notebook uses the CO2 concentration field and timestamp components from
this event-level flask product. The source file also contains uncertainty,
location, sampling-method, instrument, and NOAA quality-control fields.

## Obtaining and placing the file

The raw file is not included in this repository. Obtain the MHD surface-flask
event CO2 product from NOAA GML, using the product DOI above or the NOAA GML
data service.

From the repository root:

1. Create the local data directory if it does not already exist.

   ```bash
   mkdir -p IRE_GHG
   ```

2. Place the downloaded file at exactly:

   ```text
   IRE_GHG/co2_mhd_surface-flask_1_ccgg_event.txt
   ```

3. Keep the NOAA header intact. It records the product version, calibration
   scale, fill values, QC definitions, citation, and licensing information.

The entire `IRE_GHG/` directory is ignored by Git so the raw data are not
accidentally committed.

## Temporal scope

The NOAA product may contain observations beyond the paper period. The study
period associated with the published work ends on 2022-12-22. Analyses intended
to follow the paper should restrict the file to:

```text
1991-06-03 to 2022-12-22, inclusive
```

## NOAA revisions and recalibration

NOAA periodically recalibrates standards, revises measurements, and publishes
updated product versions. A file downloaded today may therefore differ from a
historical snapshot even when its site, product name, and observation dates are
the same. Record the download date, product version, and file checksum when
using the data, and cite the metadata embedded in that specific download.

## Data citation

The recovered file identifies the following dataset citation:

> Lan, X., G. Petron, K. Baugh, A. M. Crotwell, M. J. Crotwell, S. DeVogel,
> M. Madronich, J. Mauss, T. Mefford, E. Moglia, S. Morris, J. W. Mund,
> A. Searle, K. W. Thoning, S. Wolter, and J. Miller (2025). *Atmospheric
> Carbon Dioxide Dry Air Mole Fractions from the NOAA GML Global Greenhouse
> Gas Reference Network, Carbon Cycle Cooperative Global Air Sampling
> Network: 1967–Present*. Version 2025-08-15.
> <https://doi.org/10.15138/wkgj-f215>

Consult the header of the downloaded file for the citation appropriate to its
version. NOAA requests appropriate acknowledgement and citation when these data
support a publication. The recovered product header identifies the data as
CC0-1.0.

## Data handling note

The NOAA header declares fill values and provides a three-character QC flag.
These fields should be reviewed when interpreting the measurements. This
repository preserves the original notebook as the record of the published
exploratory workflow; it does not redistribute a transformed copy of the raw
dataset.
