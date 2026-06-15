# Phenology Article Reproducibility

This folder is a publication-ready analysis companion repository for the corrected article on European beech spring phenology in Slovenia.

Its scope is intentionally narrow and follows the article's Data availability statement:

- this repository reproduces the manuscript analyses, summary tables, and figures;
- the yearly SOS rasters are expected from Zenodo: `https://doi.org/10.5281/zenodo.20358835`;
- the accompanying Python code and reproducibility sample for Sentinel-2 time-series preprocessing, vegetation index calculation, temporal smoothing, SOS extraction, and generation of yearly SOS tables are documented separately in `https://github.com/Anapot/phenology-timeseries`.

This repository is therefore not a second copy of the full phenology extraction pipeline. It starts from the public SOS raster products plus small bundled analysis tables and focuses only on reproducing the article-level analyses.

## Article Data Availability Context

The corrected article states that:

- annual start-of-season raster maps for European beech in Slovenia, derived from Sentinel-2 IRECI time series for 2018-2021, are publicly available on Zenodo at `https://doi.org/10.5281/zenodo.20358835`;
- the accompanying Python code and reproducibility sample for the phenology extraction procedure are available at `https://github.com/Anapot/phenology-timeseries`;
- the complete Sentinel-2 national time-series archive is not redistributed because of its size and because the source Sentinel-2 data are publicly accessible through Copernicus and Sentinel Hub services.

This repository is built to sit cleanly beside that statement: it reproduces the corrected article's analyses from the public SOS outputs and from lightweight publishable inputs.

## Repository Map

- `notebooks/01_reproduce_corrected_article_analyses.ipynb`
  Main notebook for the corrected article. Section titles are written to match the manuscript results and avoid ambiguity.
- `data/external/`
  Place external inputs downloaded by the reader.
- `data/processed/`
  Lightweight bundled public tables used by the notebook.
- `data/reference/`
  Lightweight spatial reference data used for ecological-region summaries.
- `outputs/`
  Figures and tables generated when the notebook is run.
- `reference_outputs/tables/`
  Current reference tables from the corrected analysis for comparison.

## What The Reader Needs To Download

1. Zenodo SOS rasters
   Source: `https://doi.org/10.5281/zenodo.20358835`
   Expected location: `data/external/zenodo_sos_layers/`

2. Public DEM for the elevation-based analyses
   Suggested source: Copernicus DEM
   Expected location: `data/external/public_dem/`

The notebook assumes the SOS raster filenames follow the Zenodo naming used in the manuscript, for example:

- `sos_IRECI_2018_uint16_compressed.tif`
- `sos_IRECI_2019_uint16_compressed.tif`
- `sos_IRECI_2020_uint16_compressed.tif`
- `sos_IRECI_2021_uint16_compressed.tif`

## Manuscript To Notebook Mapping

- Result 1 / manuscript Section 3.1 / Figure 3
  Agreement between satellite-derived SOS and in situ observations.
  Notebook section: `Result 1 - Section 3.1 - Agreement between satellite-derived SOS and in situ observations`
  Inputs: bundled publishable agreement table in `data/processed/`

- Result 2 / manuscript Section 3.2 / Figure 4
  Altitudinal sensitivity of SOS.
  Notebook section: `Result 2 - Section 3.2 - Altitudinal sensitivity of spring onset`
  Inputs: Zenodo SOS rasters and public DEM

- Result 3 / manuscript Section 3.3 / Table 1 and regional patterns
  Ecological-region summaries, ANOVA, and elevation-plus-region regression.
  Notebook section: `Result 3 - Section 3.3 - Spatial patterns across ecological regions`
  Inputs: Zenodo SOS rasters, public DEM, bundled ecological-region layer

- Result 4 / manuscript Section 3.4
  National mean SOS anomalies.
  Notebook section: `Result 4 - Section 3.4 - Interannual variability in national mean SOS`
  Inputs: annual regional SOS table generated earlier in the notebook

- Result 5 / manuscript Section 3.5 / Figure 5
  Association between SOS variability and spring temperature.
  Notebook section: `Result 5 - Section 3.5 - Association between SOS variability and spring temperature`
  Inputs: bundled lightweight regional temperature-SOS table in `data/processed/`

## Why Some Inputs Are Bundled And Others Are Not

- The full national Sentinel-2 time-series archive is not redistributed here, matching the article's Data availability statement.
- The upstream time-series workflow and its sample reproducibility materials are maintained in the separate `phenology-timeseries` repository.
- Raw in situ phenology observations are not redistributed.
- Small derived tables needed for public figure and statistics reproduction are bundled here because they are lightweight and publishable.

## Recommended Run Order

1. Create a Python environment from `requirements.txt`.
2. Download the SOS rasters from Zenodo into `data/external/zenodo_sos_layers/`.
3. Download a public DEM into `data/external/public_dem/`.
4. Open `notebooks/01_reproduce_corrected_article_analyses.ipynb`.
5. Run the notebook from top to bottom.

## Expected Outputs

The notebook writes regenerated figures and tables into:

- `outputs/figures/`
- `outputs/tables/`

Reference tables from the current corrected analysis are already archived in `reference_outputs/tables/` so readers can compare regenerated outputs against the present repository state.
