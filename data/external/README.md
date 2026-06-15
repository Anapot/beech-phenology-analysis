# External Inputs

This directory is intentionally empty in version control.

Place the externally downloaded inputs here before running the notebook:

- `zenodo_sos_layers/`
  Contains the annual SOS rasters from `https://doi.org/10.5281/zenodo.20358835`
  These are the public yearly SOS products cited in the article's Data availability section.

- `public_dem/`
  Contains a public DEM used for the elevation-based analyses

Suggested DEM source:

- Copernicus DEM

The notebook checks these locations explicitly so the link between the code and the manuscript inputs stays unambiguous.

This directory intentionally does not store the full Sentinel-2 national time-series archive. That archive is not redistributed in the article workflow; the upstream phenology extraction procedure is documented separately in `https://github.com/Anapot/phenology-timeseries`.
