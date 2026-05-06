# Project Heimdall — Archaeological LiDAR Prospecting

**Status:** `IN PROGRESS` — Data Acquisition & Calibration Phase

---

## Purpose

This is a **self-directed learning project**. I am a Master's student in Communication Systems at KTH with a background in Computer Science, making a deliberate transition into Digital Archaeology. This project is how I am building practical skills in GIS, remote sensing, and spatial data analysis fields I have no formal training in yet. The code, methodology, and outputs will improve as my understanding develops.

Feedback from anyone working in the field is genuinely welcome.

---

## Overview

This project develops a reproducible data pipeline that transforms raw airborne LiDAR point clouds into high-contrast relief models for archaeological site identification. The target study areas are **Gamla Uppsala** and **Birka** — both well-documented Viking-age sites, which allows pipeline outputs to be validated against known features in the RAÄ Fornsök heritage register before being applied to less-surveyed terrain.

The core methodology strips away modern vegetation and infrastructure from elevation data to reveal anthropogenic subsurface features: burial mounds, stone circles, field systems, and ancient settlement foundations.

---

## Tech Stack

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Data Source** | Lantmäteriet Laserdata NH (via SLU GET portal) | High-precision Swedish LiDAR — raw `.laz` and pre-processed `.tif` |
| **Point Cloud Processing** | PDAL (Point Data Abstraction Library) | Ground filtering (Class 2), TIN-based DTM generation |
| **GIS Engine** | QGIS 3.x | Spatial analysis, layer management, and cartography |
| **Visualization** | RVT — Relief Visualization Toolbox | Sky-View Factor (SVF), Local Relief Model (LRM), Slope Gradient |
| **Scripting** | Python — GeoPandas, Rasterio | Coordinate transformations, raster clipping, pipeline automation |
| **Verification** | RAÄ Fornsök Database | Cross-referencing outputs with the Swedish National Heritage Board register |

---

## Methodology

### Step 1 — Data Acquisition
Download raw Laserdata NH (`.laz`) or pre-processed Grid 2+ CLIP (`.tif`) for the target area via the Lantmäteriet GET portal.

### Step 2 — Ground Filtering & DTM Generation
Use a PDAL JSON pipeline to isolate Class 2 (Ground) returns, removing vegetation and built structures. Convert the filtered point cloud to a Digital Terrain Model (DTM) via TIN interpolation.

### Step 3 — Relief Visualization
Apply RVT methods proven to reveal small-scale archaeological features:
- **Sky-View Factor (SVF):** Effective for burial mounds and circular depressions
- **Local Relief Model (LRM):** Effective for subtle elevation changes in flat agricultural land
- **Slope Gradient:** Effective for linear features — ancient roads, field boundaries, ramparts

### Step 4 — Validation
Overlay outputs against the RAÄ Fornsök heritage register. Known mounds serve as a benchmark; unregistered anomalies are flagged for further review.

### Step 5 — Reproducibility
The full pipeline is documented as:
- Parametric PDAL JSON files (bounding box as input variable)
- A QGIS Graphical Modeler `.model3` file for one-click execution
- An Anaconda `environment.yml` for environment replication

---



## Data Attribution

LiDAR data provided by **Lantmäteriet** via the **SLU GET portal** for academic use.
Heritage register data from **Riksantikvarieämbetet (RAÄ)** via [Fornsök](https://pub.raa.se/).
