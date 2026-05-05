## Flood Risk 

## Project Overview

This project analyzes flood-risk vulnerability in Lærdal (municipality 4642, Vestland) - a region with significant historical flood data. Using official geospatial datasets from GeoNorge, I built a reproducible pipeline to identify areas at risk under different return intervals (20, 200, and 1,000 years).

## Technical Pipeline

**Data Ingestion & Geoprocessing**

* **API Integration:** Automated fetching of municipal boundaries (Administrative Enheter) and flood zones (Flomsoner) via GeoNorge.
* **Coordinate Transformations:** Precision handling of EPSG:25832 (ETRS89 / UTM zone 32N) for accurate area calculations and EPSG:4326 for web-ready visualization.
* **Geometry Engineering:** Used shapely for advanced Polygonization of LineString boundaries and geometry validation (fixing self-intersections).

**Spatial Analysis & Clipping**

* **Spatial Operations:** Implementation of Clipping and Spatial Joins to isolate Vestland's regional flood data specifically to Lærdal's jurisdiction.
* **Quantification:** Calculation of affected areas (km²) per flood return interval to support risk-level prioritization.

## Technologies & Skills

* **Spatial Libraries:** GeoPandas, Shapely, Fiona, PyProj.

* **Data Science Stack:** Python, Pandas, NumPy, Matplotlib.

* **Geospatial Methodologies:** CRS Transformation, Polygonization, Spatial Clipping, Topology Validation, Bounding Box (BBOX) extraction.

* **Data Sources:** GeoNorge (Kartverket/NVE) APIs & GML/Vector formats.

---

## Project Structure

```text
Flood Risk/
│
├── data/
│   ├── 01_raw/                      # [Bronze] Original API outputs (ZIP/GML) via GeoNorge
│   └── 02_processed/                # [Silver Layer] Cleaned polygons & clipped flood zones (EPSG:25832)
├── notebooks/
│   ├── 01_prepare_boundary.ipynb    # Ingestion & Bronze-to-Silver processing
│   └── 02_floodzone_analysis.ipynb  # Spatial Analysis & Silver Layer refinement
│
├── results/                         # [Gold Layer] Mapping artifacts and spatial statistics
│
├── LICENSE                          
└── README.md                        
```

---

## Quick Navigation 

* [Notebook 1 – Data Collection, Inspection and Preparation](../notebooks/01_prepare_boundary.ipynb)
* [Notebook 2 – Boundary Polygonization and Flood Clipping](../notebooks/02_floodzone_analysis.ipynb)

---

## License

This project is licensed under the terms of the **MIT License**.
See the [LICENSE](./LICENSE) file for details.

---
