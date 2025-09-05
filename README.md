
# Space Time Prism (STP) Model for Measuring Accessibility of People Without Disabilities

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Python](https://img.shields.io/badge/python-3.8%2B-blue)
![Last Update](https://img.shields.io/badge/last%20update-Sep%202025-brightgreen)

## Overview

This repository provides a comprehensive workflow for modeling and analyzing daily travel behavior and accessibility for people **with & without disabilities** using the Space Time Prism (STP) Model. The workflow leverages Python and ArcGIS Pro (ArcPy) to automate spatial and network analyses, using data from the Utah Household Travel Survey.

## Table of Contents
- [Features](#features)
- [Folder Structure](#folder-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Methodological Workflow](#methodological-workflow)
- [Data Sources](#data-sources)
- [Citation](#citation)
- [Acknowledgments](#acknowledgments)

## Features
- Automated propensity score matching for group comparability
- Data cleaning and mode-specific trip extraction
- Origin-destination (OD) shapefile generation
- Service area and space-time prism (PPA) computation for multiple travel modes
- Integration of POI (Point of Interest) data and service hours
- Accessibility surface calculation and aggregation

## Folder Structure
```
PwoD STP/
  python scripts/           # Main workflow scripts (chronologically ordered)
  Data/                     # Input data (CSV, shapefiles, etc.)
  POI_Utah/                 # POI data for Utah
  ...
OD cost matrix/             # OD cost matrix and related notebooks
STP/                        # Project files and outputs
README.md                   # Project documentation
```

## Installation
1. **Clone the repository:**
	```sh
	git clone https://github.com/meghkc/Accessibility-Measures-by-using-Space-Time-Prism-Model.git
	```
2. **Set up Python environment:**
	- Python 3.8+
	- ArcGIS Pro with ArcPy
	- Required packages: `pandas`, `geopandas`, `scikit-learn`, `shapely`, etc.
	- Install dependencies:
	  ```sh
	  pip install pandas geopandas scikit-learn shapely
	  ```
3. **ArcGIS Pro:**
	- Ensure you have access to ArcGIS Pro and the necessary licenses for network analysis.

## Usage
- All scripts are in `PwoD STP/python scripts/` and are numbered to reflect the workflow order.
- Update file paths in scripts as needed for your environment.
- Run each notebook in order for a full analysis pipeline.

## Methodological Workflow
1. **Propensity Score Matching** (`0. PSM_personMatch.ipynb`):
	- Matches individuals in control/treatment groups for comparability.
2. **Data Preparation** (`1. Imprvd_pwod_csvfiles_prepn.ipynb`):
	- Cleans and processes trip data, extracts mode-specific trips.
3. **OD Shapefile Generation** (`2. Imprvd_pwod_OD_shp_prepn.ipynb`):
	- Converts CSVs to spatial shapefiles for each mode.
4. **Service Time Calculation** (`3. Allmodes_pwod_ShrtT_servTbigTsm.ipynb`):
	- Updates shapefiles with travel time and filters trips.
5. **Service Area Analysis** (`4. Allmodes_service_area_analysis.ipynb`):
	- Generates service areas for each trip/person.
6. **Potential Path Area (PPA) Calculation** (`5. Allmodes_PPA.ipynb`):
	- Computes the space-time prism for each trip.
7. **PPA Join** (`6. Allmodes_PPA_join.ipynb`):
	- Joins PPA results with origin data.
8. **POI Filtering and Analysis** (`7. ser_hr_filter_all_mode_optimized.ipynb`):
	- Integrates POI data and filters by service hours.
9. **POI Shapefile Reprojection** (`8. Allmodes_POIshp_reprojectedtoUTM.ipynb`, `8a. ...`):
	- Reprojects POI shapefiles for spatial analysis.
10. **Final Opportunity Surface Calculation** (`9. Updated_FOS_allmodes.ipynb`):
	 - Calculates accessibility surfaces for each mode.
11. **Integrated Person Daily FOS** (`10. IntegratedPersonDailyFOS.ipynb`):
	 - Aggregates daily accessibility for each person.

## Data Sources
- Utah Household Travel Survey
- POI data for Utah
- Network datasets for travel modes

## Citation
If you use this code or workflow, please cite:
```
@misc{stpmodel2025,
  author = {Megha KC},
  title = {Accessibility Measures by using Space Time Prism Model},
  year = {2025},
  url = {https://github.com/meghkc/Accessibility-Measures-by-using-Space-Time-Prism-Model}
}
```

## Acknowledgments
- Developed by Megha KC
- Built using ArcGIS Pro, Python, and open-source libraries
- Thanks to the Utah Department of Transportation for data support

---
For questions or contributions, please open an issue or pull request.
