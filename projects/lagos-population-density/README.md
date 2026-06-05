# Lagos Population Density Analysis

## Overview
This project visualizes the spatial distribution of population density across Lagos State, Nigeria, using high-resolution raster data. The goal is to identify areas of high population concentration and highlight spatial patterns relevant to urban planning and infrastructure development.

---

## Objective
To map and analyze population density across Lagos in order to:
- Identify high-density urban clusters  
- Understand spatial distribution patterns  
- Provide insight into potential pressure zones for infrastructure and services  

---

## Study Area
Lagos State, Nigeria — a rapidly growing urban region with significant population concentration in mainland and metropolitan areas.

---

## Data Sources
- WorldPop — Population raster data (100m resolution)  
- OpenStreetMap — Administrative boundary data  

---

## Methodology
The analysis was carried out using QGIS and follows a raster-based workflow:

1. Imported population raster dataset into QGIS  
2. Loaded Lagos administrative boundary (GeoJSON)  
3. Clipped population raster to the Lagos boundary  
4. Applied pseudocolor classification to represent population density  
5. Designed cartographic layout including legend, scale bar, and north arrow  
6. Exported final map for visualization  

---

## Tools & Technologies
- QGIS  
- Raster analysis techniques  
- Cartographic design principles  

---

## Output

![Lagos Population Density Map](outputs/lagos_population_map.png)

---

## Key Insights
- High population density is concentrated in mainland Lagos, particularly in central-western urban zones  
- Peripheral regions exhibit significantly lower population density  
- The spatial pattern suggests uneven distribution of population, with implications for infrastructure demand, transportation planning, and service delivery  

---

## Limitations
- Population data is modeled and may not reflect real-time distribution  
- Resolution (100m) may generalize micro-level variations  
- Boundary data accuracy depends on OpenStreetMap contributions  

---

## Future Improvements
- Integrate administrative-level aggregation (e.g., LGAs)  
- Perform temporal analysis to track urban expansion  
- Combine with infrastructure datasets (roads, healthcare, schools) for accessibility analysis  
- Develop an interactive web map version  

---

## Author
Samson Adeyomoye

---

## Project Status
Completed ✔
