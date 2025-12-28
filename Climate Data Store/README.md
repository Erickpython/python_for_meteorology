# 🌧️ ERA5 Total Precipitation — 01–04 Dec 2024

**Clear, reproducible workflow to download, process, and visualize ERA5 total precipitation (tp) for Kenya** using the Copernicus Climate Data Store (CDS) API and Python.

---

## 📌 Overview
This repository contains a Jupyter Notebook (`download_era5_rain.ipynb`) that:

- Downloads ERA5 total precipitation (`tp`) for Kenya for **2024-12-01 → 2024-12-04** using the `cdsapi` client.
- Loads the NetCDF data with `xarray` (the data are multi-dimensional, time/lat/lon).
- Plots precipitation maps for each timestamp over Kenya.
- Converts precipitation from **meters → millimeters** (×1000), computes mean rainfall per timestamp, and aggregates to daily totals.
- Extracts a point time series (e.g., **Nairobi**) and converts it to a `pandas` `DataFrame` for downstream ML or analysis.

---

## �� Quick Start
1. Install dependencies:

```bash
pip install cdsapi xarray netCDF4 numpy pandas matplotlib
```

2. Configure your CDS API key in `~/.cdsapirc`:

```
url: https://cds.climate.copernicus.eu/api/v2
key: <your-uid>:<your-api-key>
```

3. Open `download_era5_rain.ipynb` and run cells in order.

---

## 🔧 Key Steps (what the notebook does)

- Request data from CDS using dataset: `reanalysis-era5-single-levels` and variable `total_precipitation`.
- Area bounding box used: **[6, 33, -5, 42]** (Kenya extent).
- Load the returned NetCDF with `xarray` and inspect `ds['tp']`.
- Convert units: `rain_mm = ds['tp'] * 1000` (m → mm).
- Compute per-timestep mean: `mean_rain = rain_mm.isel(valid_time=i).mean().values`.
- Aggregate daily totals: `daily_rain = rain_mm.resample(valid_time='1D').sum()`.
- Extract a point (example: Nairobi):

```python
nairobi_rain = daily_rain.sel(latitude=-1.29, longitude=36.82, method='nearest')
df = nairobi_rain.to_dataframe(name='nairobi_rainfall_mm')
```

- Plot maps per timestamp and a time series for the chosen point.

---

## 📈 Results & Insights
- Time-slice maps visualize how rainfall varied across Kenya at each timestamp.
- Unit conversion and daily aggregation make interpretation and further analysis intuitive.
- Point extraction (e.g., Nairobi) produces a clean `DataFrame` ready for ML or statistical modeling.

---

## 📂 Files
- `download_era5_rain.ipynb` — notebook with full pipeline (download → analyze → plot)
- `era5_total_precipitation_dec_2024.nc` — example NetCDF output (downloaded data)

---

## 💡 Next Steps / Ideas
- Save point time series (CSV) for ML workflows.
- Expand date range or add additional variables (temperature, humidity).
- Create automated scripts or parameterize the notebook for batch runs.
- Produce climatologies or anomaly maps.

---

## 📜 Acknowledgements
- Data courtesy of the Copernicus Climate Data Store (ERA5).

---

*This notebook was a learning exercise in using Python to access, manipulate, and prepare meteorological data (cdsapi, xarray, netCDF4, numpy, pandas, matplotlib).* 

