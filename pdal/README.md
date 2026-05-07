# PDAL Pipelines

This folder contains the PDAL JSON pipeline files for Project Heimdall.
Run them in order

---

## Files

### `01_ground_filter.json`
Filters a raw `.laz` point cloud to retain only Class 2 (Ground) points,
removing vegetation, buildings, and all above-ground returns.

```bash
pdal pipeline pdal/01_ground_filter.json
```

---

### `02_rasterize.json`
Converts a ground-only `.laz` point cloud into a Digital Terrain Model (DTM)
GeoTIFF using IDW (Inverse Distance Weighting) interpolation at 0.5m resolution.

The output is projected to SWEREF99TM (EPSG:3006) — the Swedish national
coordinate system used by Lantmäteriet.

```bash
pdal pipeline pdal/02_rasterize.json
```

---

### `03_full_pipeline_parametric.json`
 in progress
---



---

## Resolution Guide

| Resolution | Pixel size | Best for |
|-----------|------------|---------|
| `1.0` | 1m × 1m | Large area overview, fast processing |
| `0.5` | 0.5m × 0.5m | Standard  |
| `0.25` | 0.25m × 0.25m | Fine detail best for small areas |

---



## Notes
