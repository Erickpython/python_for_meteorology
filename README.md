# Meteorology Learning — Nowcasting with WRF‑ARW

This repository documents a focused learning journey in meteorology with emphasis on nowcasting using the WRF‑ARW model. It contains Jupyter notebooks, scripts and example data for acquiring and processing atmospheric model outputs (GFS 0.25° from NOAA NOMADS and ERA5 from the Copernicus Climate Data Store), basic preprocessing, simple prediction experiments, and WRF output visualization.

## Contents (high level)
- Notebooks and scripts to download and process model and reanalysis data.
- Example workflows for:
  - Downloading and handling GFS 0.25° data from NOAA NOMADS.
  - Downloading and processing ERA5 total precipitation (CDS).
  - Preparing data for simple rainfall models (Nairobi example).
  - Visualizing WRF output and building simple WRF-based nowcasts.

## Key files / notebooks
- [wrf_data.ipynb](wrf_data.ipynb) — data download and preparation for WRF/GFS/ERA5
- [wrf model simukations/wrfpy.ipynb](wrf model simukations/wrfpy.ipynb) — WRF processing / visualization examples
- [Climate Data Store/download_era5_rain.ipynb](Climate Data Store/download_era5_rain.ipynb) — ERA5 TP download and aggregation
- [Rainfall Prediction/simple_rainfall_predict_model.ipynb](Rainfall Prediction/simple_rainfall_predict_model.ipynb) — simple rainfall prediction workflow
- [WRF_OUTPUT_VISUALIZATION/09_01_2025/wrf.ipynb](WRF_OUTPUT_VISUALIZATION/09_01_2025/wrf.ipynb) — visualization examples
- [requirements.txt](requirements.txt) — environment dependencies

## Quick start
1. Create and activate a Python venv.
2. Install dependencies:
   pip install -r requirements.txt
3. Open the desired notebook in Jupyter / JupyterLab / VS Code and follow cells in order.

## Notes on data sources
- GFS 0.25° data: downloaded from NOAA NOMADS (processed to the formats used by the notebooks).
- ERA5 (total precipitation): retrieved using Copernicus Climate Data Store (cdsapi) and processed with xarray/pandas.

## Collaboration & contact
For collaboration, questions or suggestions, please contact:
- Email: erick.wambugu23@gmail.com  
- LinkedIn: https://www.linkedin.com/in/erick-wambugu-425a15161/

Contributions are welcome — open an issue or reach out directly.

## License
MIT License — please see individual notebooks and files for attribution notes where applicable.