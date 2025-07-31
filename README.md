# USA Transportation Project

This project analyzes and visualizes the U.S. passenger and freight rail networks alongside metro areas and airports to identify and rank potential high-speed rail corridors.
It integrates spatial datasets from federal sources, calculates corridor scores based on population interaction and distance, and produces interactive web maps and GeoJSON outputs.

---

## 📁 Project Structure
```
USA_TRANSPORTATION_PROJECT/
├── Data/
│ ├── NTAD_Amtrak_Routes_/Amtrak_Routes.shp
│ ├── NTAD_Amtrak_Stations_/Amtrak_Stations.shp
│ ├── NTAD_Aviation_Facilities_/Aviation_Facilities.shp
│ ├── NTAD_North_American_Rail_Network_Lines_/North_American_Rail_Network_Lines.shp
│ ├── tl_2023_us_cbsa/tl_2023_us_cbsa.shp
│ ├── tl_2023_us_state/tl_2023_us_state.shp
│ └── places_usa_2023.gpkg
│
├── Output/
│ ├── corridor_output_log.txt
│ ├── corridors_top100.geojson
│ └── north_america_rail_air_metro_corridors_pop_weighted_final.html
│
├── USA_Rail_Lines_Stations_Corridors (map & corridor CSVs).py
├── .gitattributes
├── .gitignore
```

---

## Features

- Loads and processes shapefiles for:
  - Amtrak routes and stations
  - Freight rail network
  - Aviation facilities
  - CBSAs and U.S. states
- Computes corridor desirability using a population-based interaction score
- Densifies geometries for better curvature estimates and visualization
- Outputs:
  - A top 100 ranked corridor GeoJSON
  - An interactive Folium map
  - A processing log

---

## Scoring Methodology

Each candidate corridor is scored using:

Score = (Population_A × Population_B) / Distance²

Only corridors between 100–500 miles are considered. Anchors are population-weighted CBSA centroids derived from 2023 TIGER/Line and ACS data.

---

## Requirements

Install required packages via pip:

```bash
pip install geopandas folium branca shapely pyproj pandas
```

Other system-level requirements:

GDAL/OGR (for reading shapefiles)
Git LFS (for handling large files tracked in this repo)

How to Run

Run the main script:

```
python "USA_Rail_Lines_Stations_Corridors (map & corridor CSVs).py"

```

This will:

Load and process geospatial data
Compute and score corridors
Generate corridors_top100.geojson
Create north_america_rail_air_metro_corridors_pop_weighted_final.html map in Output/

Data Sources
```
National Transportation Atlas Database (NTAD)
U.S. Census TIGER/Line Shapefiles (2023)
American Community Survey (ACS) Place-Level Population
```


Notes

Large files (e.g., .gpkg, .html, .shp) are tracked via Git LFS.
GitHub blocks files over 100 MB in standard Git—please install Git LFS:

```
git lfs install

```

Outputs are viewable locally (e.g., in a browser or GIS software).


### Data Licensing

This project uses datasets published by the U.S. federal government (e.g., NTAD, TIGER/Line) which are public domain under 17 U.S.C. § 105. 
These datasets are not protected by copyright and are freely available for public use.
