## Flood Risk 

## Project Overview

This independent project analyzes flood-risk zones in Lærdal municipality (kommune **4642**, Vestland) using official, open geospatial datasets from **GeoNorge**. The goal is to identify areas at greatest risk of flooding under different return intervals (**20**, **200**, and **1,000** years), supporting local planning, civil protection, and the future development of alert systems.

## Technical Pipeline

**Notebook 1 - Data Collection, Inspection and Preparation**

* Fetch official municipal boundary from GeoNorge (HTTP → ZIP).
* Extract vectors and load as a `GeoDataFrame` (GeoPandas).
* Inspect geometry, reproject (analysis CRS: **EPSG:25832**; web viz: **EPSG:4326**).
* Export cleaned **boundary lines** and store **bbox/centroid** metadata for reuse.

**Notebook 2 - Boundary Polygonization and Flood Clipping**

* Load boundary **LineString** geometry and convert to **Polygon** (`shapely.ops.polygonize`).
* Validate geometry and compute municipality area (km²) in **EPSG:25832**.
* Query/download Vestland **flomsoner** (flood zones, GML) from GeoNorge.
* Normalize and reproject layers; **clip** flood zones to the Lærdal polygon.
* Export clipped layers for mapping and statistics (analysis/web).

## Technologies Used

**Languages & Libraries:** Python · Pandas · GeoPandas · Shapely · Fiona · Matplotlib · Requests · Pathlib
**Spatial I/O:** GDAL/OGR (via GeoPandas/Fiona)
**Data Sources:** Official open datasets from **GeoNorge.no**
**Workflow:** Jupyter Notebooks · Modular, auditable folder structure · Version-controlled pipeline (Git)

**Methods**

* Download and process official municipal boundaries from GeoNorge.
* Convert **LineString** geometries to **Polygon** for accurate spatial operations.
* Load and **clip** the *FlomAreal* flood-zone layer to the Lærdal boundary.
* Reproject to analysis (**EPSG:25832**) and web visualization (**EPSG:4326**).
* Explore schema/attributes and prepare artifacts for mapping and statistics.

---

## Project Structure

```text
Flood Risk/
│
├── data/
│   ├── 01_raw/                      # download via Notebook 1 (GeoNorge APIs/ZIP)
│   └── 02_processed/                # boundary lines, polygon, centroid, bbox, and flood zones 
│
├── notebooks/
│   ├── 01_prepare_boundary.ipynb    # Data collection and inspection
│   └── 02_floodzone_analysis.ipynb  # Boundary polygonization and flood clipping
│
├── results/                         # quick-look PNGs, previews for boundary/floodzones
│
├── LICENSE                          # MIT License
└── README.md                        # project description and usage guide
```

---

## Author

**Tássia Tavares**

**Academic Background**

* PhD in Chemistry with a background in environmental chemistry, biochemistry, and biotechnology.

**Professional Strengths**

* Specialist in **interdisciplinary projects**.
* Experienced with **complex datasets, statistical analysis, and ML-ready pipelines**.

**Data Science**

* Certified in **Python for Data Science, AI and Development (IBM)**.
* Delivers end-to-end, reproducible data products from ingestion and QA to feature engineering, modeling, and decision ready reporting applied to complex, real-world, science driven problems.

[![LinkedIn](https://img.shields.io/badge/Connect-LinkedIn-blue.svg?logo=linkedin)](https://www.linkedin.com/in/tassia-/)

---

## Navigation Links

* [Notebook 1 – Data Collection, Inspection and Preparation](../notebooks/01_prepare_boundary.ipynb)
* [Notebook 2 – Boundary Polygonization and Flood Clipping](../notebooks/02_floodzone_analysis.ipynb)

---

## License

This project is licensed under the terms of the **MIT License**.
See the [LICENSE](./LICENSE) file for details.

---
