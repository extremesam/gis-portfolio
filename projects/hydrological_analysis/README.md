Hydrological Analysis: Flow Paths and Watersheds
Delineate watersheds and model hydrological flow using Digital Elevation Models in QGIS

A comprehensive guide to hydrological analysis including flow direction, flow accumulation, watershed delineation, stream networks, and drainage basin analysis using QGIS and terrain data
Author
GIS Tutorial Team

Published
February 5, 2025

 Tutorial: Hydrological Analysis - Flow Paths & Watersheds
Master hydrological analysis by delineating watersheds, calculating flow paths, and analyzing drainage networks from Digital Elevation Models.

100 minutes

Advanced

GIS Hydrology Watershed QGIS

 Learning Objectives
By the end of this tutorial, you will be able to:

Objective 1 {#obj-1}: Calculate flow direction and flow accumulation from a DEM → Go to Step 1
Objective 2 {#obj-2}: Delineate watersheds and drainage basins → Go to Step 2
Objective 3 {#obj-3}: Extract and classify stream networks → Go to Step 3
Objective 4 {#obj-4}: Calculate watershed morphometric parameters → Go to Step 4
Objective 5 {#obj-5}: Perform hydrological analysis and modeling → Go to Step 5
These skills are essential for water resource management, flood risk assessment, environmental planning, stream restoration, and hydrological modeling.

📍 Learning Path: Objectives → Steps
Objective	Related Step	Time	Key Outcome
🎯 Calculate flow direction	Step 1: Flow Direction & Accumulation	20 min	Flow rasters
🎯 Delineate watersheds	Step 2: Watershed Delineation	20 min	Watershed polygons
🎯 Extract streams	Step 3: Stream Networks	20 min	Stream vector network
🎯 Calculate parameters	Step 4: Morphometric Analysis	20 min	Basin statistics
🎯 Perform modeling	Step 5: Hydrological Modeling	20 min	Flow paths & analysis
 Workflow Summary
This tutorial follows these key steps:

┌─────────────────────────────────────────────────────┐
│ STEP 1: Flow Direction & Accumulation               │
│ What: Calculate D8 flow routing algorithm           │
│ Time: ~20 min                                       │
└──────────────────────┬──────────────────────────────┘
                       ↓
┌─────────────────────────────────────────────────────┐
│ STEP 2: Watershed Delineation                       │
│ What: Define drainage basins from outlet points     │
│ Time: ~20 min                                       │
└──────────────────────┬──────────────────────────────┘
                       ↓
┌─────────────────────────────────────────────────────┐
│ STEP 3: Stream Network Extraction                   │
│ What: Generate stream vectors from flow accum.      │
│ Time: ~20 min                                       │
└──────────────────────┬──────────────────────────────┘
                       ↓
┌─────────────────────────────────────────────────────┐
│ STEP 4: Morphometric Analysis                       │
│ What: Calculate basin shape and characteristics     │
│ Time: ~20 min                                       │
└──────────────────────┬──────────────────────────────┘
                       ↓
┌─────────────────────────────────────────────────────┐
│ STEP 5: Hydrological Modeling                       │
│ What: Model water movement and flood risk           │
│ Time: ~20 min                                       │
└──────────────────────┬──────────────────────────────┘
                       ↓
┌─────────────────────────────────────────────────────┐
│ RESULT: Complete hydrological analysis package      │
└─────────────────────────────────────────────────────┘
 Prerequisites & Requirements
Before you start, make sure you have:

QGIS 3.x or higher with GDAL/OGR tools and SAGA integration
High-quality DEM (LiDAR preferred, SRTM acceptable for large regions)
Preprocessed DEM with sinks filled (critical for hydrology!)
Outlet point shapefile (for watershed delineation)
~500 MB free disk space for processing
TauDEM plugin or SAGA tools installed (for advanced hydrology)
Knowledge assumed: - Completion of “Working with Terrain Data” tutorial - Understanding of flow routing concepts - Familiarity with raster calculator - Basic watershed hydrology knowledge

⚠️ Critical: DEM must have sinks filled before hydrological analysis. Unfilled sinks trap water and create incorrect flow paths!

 Data & Resources
What you need:

Resource	Type	Purpose
DEM (sinks filled)	GeoTIFF raster	Input for flow calculations
Outlet point	Vector shapefile	Pour point for watershed
Study area boundary	Vector shapefile	For clipping outputs
QGIS SAGA Tools	Plugin	Advanced hydrology functions
Optional software: - TauDEM — Specialized hydrological analysis (free) - WhiteboxTools — Modern watershed analysis (free) - GDAL — Command-line raster tools

Data sources: - USGS National Hydrography Dataset: https://www.usgs.gov/mission/water-resources/ - OpenTopography DEM: https://www.opentopodata.org/ - Local hydrological data: Regional water authorities

 Step-by-Step Instructions
Step 1: Flow Direction & Accumulation
Step 2: Watershed Delineation
Step 3: Stream Networks
Step 4: Morphometric Analysis
Step 5: Hydrological Modeling
Achieves: ✅ Learning Objective 1: Calculate flow direction and accumulation

What you’ll do: Calculate D8 flow routing to determine how water moves across the terrain.

1.1 — Understanding Flow Direction (D8 Algorithm)
The D8 (8-direction) algorithm routes water from each cell to one of its 8 neighbors (including diagonals). Water always flows to the lowest neighbor elevation.

1.2 — Fill DEM Sinks (Critical Step!)
First, you must remove “sinks” — cells where water would be trapped:

QGIS Processing Toolbox

Search for “Fill Sinks” (SAGA):

Configuration:

Parameter	Setting
DEM	dem_clipped.tif
Output	dem_filled.tif
This creates a depression-free DEM where water can flow continuously to outlets.

Two DEM maps side-by-side comparing original with many pits and sink-filled version

1.3 — Calculate Flow Direction
QGIS Processing Toolbox

Search for “Catchment Area” or “Flow Direction” (SAGA):

Configuration:

Parameter	Setting
DEM	dem_filled.tif
Algorithm	D8 (8-direction)
Output	flow_direction.tif
Flow direction values (1-256): - 1 = East, 2 = Southeast, 4 = South, 8 = Southwest - 16 = West, 32 = Northwest, 64 = North, 128 = Northeast

1.4 — Calculate Flow Accumulation
Flow accumulation counts how many upslope cells drain to each cell. High accumulation = concentrated flow (streams).

QGIS Processing Toolbox

Search for “Catchment Area” (SAGA):

Configuration:

Parameter	Setting
DEM	dem_filled.tif
Algorithm	D8
Output	flow_accumulation.tif
Interpreting flow accumulation: - Values 1-10 = hillslopes (dispersed flow) - Values 10-100 = small streams - Values 100-1000 = medium streams - Values >1000 = major rivers

Two maps showing flow direction vectors and flow accumulation as colored heatmap with blue=high accumulation

← Back to Learning Objectives

 Result & Expected Outcome
What you should have now:

✅ Flow direction raster (D8 flow paths)
✅ Flow accumulation raster (concentration zones)
✅ Watershed polygon (drainage basin boundary)
✅ Stream network (vector and classified by order)
✅ Morphometric parameters (basin characteristics)
✅ Hydrological indices (TWI, SPI, flood risk)

Your complete hydrological analysis package:

hydrological_analysis/
├── flow_analysis/
│   ├── dem_filled.tif
│   ├── flow_direction.tif
│   ├── flow_accumulation.tif
│   └── upslope_area.tif
├── watershed/
│   ├── watershed.tif
│   ├── watershed_polygon.shp
│   └── outlet_snapped.shp
├── streams/
│   ├── streams_raster.tif
│   ├── streams_vector.shp
│   ├── stream_order.tif
│   ├── headwater_streams.shp
│   └── main_channel.shp
├── morphometrics/
│   ├── basin_parameters.csv
│   ├── stream_statistics.csv
│   └── basin_summary_table.xlsx
├── hydro_indices/
│   ├── topographic_wetness_index.tif
│   ├── stream_power_index.tif
│   ├── flow_path_length.tif
│   └── time_to_concentration.tif
└── hazard_assessment/
    ├── flood_potential.tif
    ├── landslide_susceptibility.tif
    └── erosion_risk_zones.shp
Applications of your hydrological analysis: - 💧 Water resource management & allocation - 🌊 Flood risk assessment & mapping - 🌍 Environmental flow requirements - 📍 Optimal stream gauge placement - 🚣 Erosion and sediment transport modeling - 💩 Wastewater dispersion modeling - 🏗️ Infrastructure planning (dams, bridges) - 🌿 Riparian restoration planning

 Exercises & Challenges
Challenge 1: Advanced — Multi-Outlet Watershed Analysis
🔴 Complex Basin Delineation Advanced

Objective: Delineate multiple nested watersheds and analyze their characteristics.

Your task:

Create 3 outlet points at different locations in your study area
Delineate 3 watersheds from these outlets
Calculate morphometric parameters for each watershed
Compare basin characteristics and hydrological response
Identify which basin is most flood-prone based on morphometrics
Document differences and explain hydrological implications
Hint: Use bifurcation ratios and drainage density as flood risk indicators.

Solution (click to reveal):

Tip
Challenge 2: Advanced — Streamflow Routing & Time to Peak
🔴 Flow Path Length & Concentration Time Advanced

Objective: Calculate flow path length and estimate time-to-peak streamflow response.

Your task:

Create flow path length raster (distance from each cell to outlet)
Calculate concentration time using Kirpich equation
Map hydrological response zones (fast vs. slow)
Determine lag time between rainfall and peak discharge
Identify critical flow paths contributing most to peak flow
Compare concentration times across different altitudes
Resources: - Kirpich equation: Tc = 0.0078 * L^0.77 * S^-0.385 (L=path length km, S=slope)

 Tips, Tricks & Warnings
💡 Pro Tips
Tip 1: Always fill sinks first! Unfilled DEMs create “phantom watersheds” and false streams. This is the #1 hydrology mistake.

Tip 2: Choose flow accumulation threshold carefully — Too low = too many streams. Too high = misses headwaters. Start with 100 cells, adjust based on visual inspection.

Tip 3: Validate streams against observed data — Compare your extracted streams to USGS hydrography data or field observations. Significant differences indicate DEM issues.

Tip 4: Use high-quality DEMs — SRTM works for large basins (>100 km²). Use LiDAR for detailed stream networks and small watersheds (<10 km²).

Tip 5: Consider flow direction algorithms — D8 is standard but creates “flow artifacts” on flat terrain. Use D∞ (infinite) for better results on complex terrain.

Tip 6: Document your threshold choices — Different flood studies used different flow accumulation thresholds. Always document your choices for reproducibility.

⚠️ Common Pitfalls
Watch out for these mistakes:

Skipping sink filling: Sinks trap water and completely corrupt flow routing. Always fill sinks first!

❌ Flow raster without filling = phantom streams everywhere
✅ Filled DEM = realistic flow paths
Using original DEM instead of filled: Flow routing requires a hydrologically correct DEM with no internal depressions.

Wrong flow accumulation threshold: Too many or too few streams = wrong watershed delineation and false flood modeling.

Threshold too low:   100 cells  = many small streams
Threshold correct:   1000 cells = realistic network
Threshold too high:  10000 cells = misses headwaters
Ignoring DEM resolution effects — 30m DEM may miss small streams visible in 5m LiDAR. Results are NOT directly comparable!

Misinterpreting morphometric parameters — High drainage density ≠ always bad. It varies by geology and climate.

🔴 Critical Warnings
These mistakes can invalidate your entire analysis:

⚠️ Never use geographic coordinates (lat/lon) for hydrological analysis! Flow routing calculates distances and slopes that are meaningless in geographic CRS:

❌ WRONG: Flow distance in WGS 84 lat/lon = incorrect distances
✅ CORRECT: Use projected CRS (UTM or local projection)
Always reproject to projected coordinate system before any flow calculations.

⚠️ Check for data voids and artifacts — SRTM has missing data over water, clouds, and mountains. LiDAR may have classification errors. Always inspect your DEM before hydrology!

⚠️ Validate against field data — Computer models can be wrong! Compare your delineated watershed to: - USGS gauging station locations - Published watershed maps - Ground survey data

Never rely solely on DEM analysis for critical applications (flood risk, water supply design).

 Related Tutorials & Next Steps
After completing this tutorial, you might be interested in:

Level Up Your Skills
Advanced Flood Modeling: 2D Inundation Mapping — Create detailed flood maps using QGIS and GDAL
Estimated time: 120 minutes
Difficulty: Advanced
Sediment Transport & Channel Erosion — Model erosion and deposition using hydrology
Estimated time: 90 minutes
Difficulty: Advanced
Groundwater Analysis from Topography — Estimate groundwater flow using terrain
Estimated time: 75 minutes
Difficulty: Advanced
Related Topics
Snow Accumulation Modeling — Use terrain to predict snow distribution
Contaminant Transport — Model pollutant movement using flow paths
Spring Delineation — Find groundwater emergence points
Water Quality Assessment — Analyze pollution distribution in watersheds
Riparian Vegetation Modeling — Link hydrological indices to plant communities
Practice Projects
Project 1: Delineate local watershed and compare to official boundaries
Project 2: Model flood risk for a river reach
Project 3: Design stream restoration using hydrological analysis
Project 4: Assess water supply potential for a region
 References & Further Reading
Official Documentation
QGIS SAGA Tools Manual: https://docs.qgis.org/latest/en/docs/user_manual/processing_algs/qgis/index.html
GDAL Raster Functions: https://gdal.org/python/osgeo_gdal_gdalconst.html
TauDEM Documentation: https://hydrology.unsw.edu.au/download/taudem/
Academic References
“Hydrologic and Hydraulic Modeling Support with Geographic Information Systems” — Maidment et al. (2002)
Definitive guide to watershed analysis with GIS
Explains D8, flow accumulation, and morphometrics
“Principles of Watershed Delineation” — USGS Water Resources (1989)
Technical standards for watershed boundaries
Explains hydrological concepts clearly
“Catchment Characteristics and Runoff” — McDonnell & Woods (2004)
How basin properties affect flood response
Links morphometrics to hydrology
Online Resources & Datasets
USGS National Hydrography Dataset: https://www.usgs.gov/ngp/National-Hydrography-Dataset
Official US stream networks for validation
USGS WaterWatch: https://waterwatch.usgs.gov/
Real-time streamflow data to validate your models
OpenTopography: https://www.opentopodata.org/
Free global LiDAR and DEM access
Google Earth Engine: https://earthengine.google.com/
Cloud-based watershed and hydrology tools
Tools & Software
QGIS — Main tool (free, open-source)
SAGA GIS — Specialized terrain/hydrology (free)
TauDEM — Terrain Analysis Using Digital Elevation Models (free)
WhiteboxTools — Modern GIS toolkit (free, fast)
ArcGIS Spatial Analyst — Commercial but powerful
Kirpich Formula & Alternatives
Concentration Time Estimation:

Kirpich:      Tc = 0.0078 * L^0.77 * S^-0.385
California:   Tc = 0.0195 * L^0.77 * S^-0.385  (steeper)
SCS:          Tc = 0.0078 * L^0.8 / S^0.5      (varies by surface)

Where: Tc = concentration time (hours)
       L = flow path length (km)
       S = average slope (decimal fraction)
 Questions or Issues?
If you encounter problems:

Check sink filling — Most hydrology issues trace back to unfilled sinks
Verify CRS — Confirm you’re using projected coordinates (UTM)
Inspect DEM — Look for artifacts, voids, or data anomalies
Compare to USGS data — Validate your streams and watersheds against official data
Review QGIS documentation — https://docs.qgis.org/
Common issues & solutions:

Issue	Solution
Streams don’t match observed	Lower flow accumulation threshold or fill sinks better
Watershed boundary crosses ridge	Wrong outlet point or unfilled sinks — re-snap outlet
Flow direction looks random	DEM not filled or wrong CRS (using lat/lon)
Morphometrics unrealistic	Check basin area calculation — may need unit conversion
TWI has negative values	Normal! Values are log-transformed. Use for relative comparison
