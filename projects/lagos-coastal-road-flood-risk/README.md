# Lagos Coastal Road Flood Risk Analysis (2km Corridor Study)

This project presents a geospatial flood risk assessment of the Lagos Coastal Road corridor using a 2 km buffer. The goal is to identify and quantify flood-prone areas using elevation and terrain analysis.
The study focuses on a 2 km buffer along the Lagos Coastal Road corridor, covering approximately 299 km² within the Lekki–Eleko coastal axis.

- DEM clipped to study area
- Elevation classification:
  - ≤2m (High Risk)
  - 2–5m (Medium Risk)
  - >5m (Low Risk)
- Raster to polygon conversion
- Area calculation per class
- Slope analysis for terrain validation

| Risk Level | Area (km²) | Percentage |
|-----------|-----------|------------|
| High Risk | 20.79 | 6.95% |
| Medium Risk | 63.81 | 21.34% |
| Low Risk | 214.39 | 71.71% |

- Flood risk is spatially concentrated, not uniform
- ~28% of the corridor is moderately to highly vulnerable
- High-risk zones align with low-elevation and low-slope terrain
- Critical exposure exists along the Lekki–Eleko axis

This analysis is based on elevation and terrain only. It does not include rainfall data, drainage systems, or hydrodynamic modeling.

![Flood Risk Map](maps/flood_risk_map.png)

- QGIS
- DEM (SRTM / OpenTopography)
- Raster Analysis
- Vector Processing

This analysis can support:
- Infrastructure planning
- Flood risk mitigation strategies
- Urban development control along coastal corridors
