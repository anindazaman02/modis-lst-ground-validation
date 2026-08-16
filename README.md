# Ground Validation of MODIS Land Surface Temperature Against BMD Station Data

This repository contains an R script used to validate satellite-derived Land Surface Temperature (LST) against ground-level meteorological observations. The pipeline pairs annual Daytime MODIS Aqua LST retrievals with Maximum Air Temperature records from the Bangladesh Meteorological Department (BMD) spanning 2003–2025.

The script computes standard statistical validation metrics and generates a publication-ready 1:1 scatter plot with an orthogonal 1:1 reference line.

---

## What the Script Does

1. **Loads validation data:** Ingests paired annual ground station temperatures (`BMD_Air_Temp`) and satellite thermal observations (`MODIS_LST`) from Excel (`LST_Validation_Annual.xlsx`).
2. **Computes error and correlation metrics:**
   * **Pearson Correlation ($r$) & Coefficient of Determination ($R^2$):** Measures the linear association and explained variance between station records and satellite observations.
   * **Root Mean Square Error (RMSE):** Calculates the average magnitude of absolute error (°C).
   * **Mean Bias Error (MBE):** Evaluates overall satellite under- or over-estimation relative to in-situ records.
3. **Builds a 1:1 validation scatter plot:** Uses `ggplot2` with a fixed 1:1 aspect ratio (`coord_fixed`) to display:
   * A **1:1 agreement line** (dashed gray) representing perfect model-to-ground alignment.
   * A **fitted linear regression line** (solid red) capturing actual empirical correspondence.
   * On-plot statistical annotation of $R^2$, RMSE, and $p$-value.
4. **Exports high-resolution figures:** Saves a 300 DPI square graphic (`LST_Validation_Plot.png`) for direct inclusion in thesis documentation or journal submissions.

---

## Required Packages

Install the following R libraries before executing the script:

```r
install.packages(c("readxl", "ggplot2"))
