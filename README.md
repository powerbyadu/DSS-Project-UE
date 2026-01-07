🔥 WILDFIRE PREDICTION USING SATELLITE IMAGERY & MACHINE LEARNING
===============================================================

This project implements an end-to-end wildfire prediction system using
MODIS satellite data, Google Earth Engine (GEE), and Machine Learning.
The system predicts wildfire occurrence at pixel level and evaluates
performance using both statistical metrics and spatial error analysis.

---------------------------------------------------------------
PROJECT OBJECTIVES
---------------------------------------------------------------
- Extract vegetation indices (NDVI, EVI) from MODIS satellite data
- Generate wildfire labels using MODIS Burned Area product
- Train and compare ML models (Random Forest, XGBoost)
- Predict wildfire occurrence for every pixel in the study area
- Perform spatial validation using confusion matrix logic (TP, TN, FP, FN)

---------------------------------------------------------------
KEY CONCEPTS USED
---------------------------------------------------------------
- Remote Sensing (MODIS)
- Vegetation Indices (NDVI, EVI)
- Google Earth Engine (Cloud-based geospatial processing)
- Machine Learning
- Confusion Matrix
- Raster-based spatial validation

---------------------------------------------------------------
PROJECT STRUCTURE
---------------------------------------------------------------
wildfire-prediction/
│
├── main.py
├── gee_processing.py
├── ml_training.py
├── raster_validation.py
├── requirements.txt
├── README.md
└── outputs/
    ├── WF_RF_PRED_BC_2023.tif
    ├── WF_TRUE_BURN_BC_2023.tif
    └── Error_Map_TP_TN_FP_FN.png

---------------------------------------------------------------
SYSTEM REQUIREMENTS
---------------------------------------------------------------
- Python 3.8 or higher
- Internet connection
- Google Earth Engine account (Personal / Academic)

---------------------------------------------------------------
LIBRARIES & API INSTALLATION (DETAILED)
---------------------------------------------------------------

The following libraries are installed and used in this project.
Some libraries work locally on the system, while others act as APIs
to connect with cloud-based services.

INSTALLATION COMMAND:
,,bash
pip install numpy pandas matplotlib rasterio scikit-learn folium earthengine-api
,,,

---------------------------------------------------------------
1) GOOGLE EARTH ENGINE PYTHON API (earthengine-api)
---------------------------------------------------------------

TYPE:
- Cloud API (installed locally as a Python library)

PURPOSE:
- Connects Python code to Google Earth Engine servers
- Accesses large satellite datasets (MODIS)
- Performs geospatial processing in the cloud

WHY IT IS REQUIRED:
- Satellite data is too large to process locally
- GEE handles data storage, computation, and exports

HOW IT IS USED:
- Data extraction (NDVI, EVI)
- Fire label generation
- Training ML model inside Earth Engine
- Exporting GeoTIFF outputs

AUTHENTICATION METHOD:
- Token-based authentication
- Personal / Academic use (free)

IMPORTANT NOTE:
- This API is free for personal and academic use
- Commercial use requires billing

---------------------------------------------------------------
2) NUMPY
---------------------------------------------------------------

TYPE:
- Local Python library

PURPOSE:
- Numerical computation
- Array and matrix operations

WHY IT IS REQUIRED:
- Raster data is stored as arrays
- Pixel-wise comparisons and calculations

HOW IT IS USED:
- Binary conversion of rasters (0/1)
- Error map creation (TP, TN, FP, FN)
- Metric calculations (accuracy, precision, recall)

---------------------------------------------------------------
3) PANDAS
---------------------------------------------------------------

TYPE:
- Local Python library

PURPOSE:
- Tabular data handling

WHY IT IS REQUIRED:
- Training data exported from Earth Engine is in CSV format

HOW IT IS USED:
- Reading CSV datasets
- Cleaning and preprocessing data
- Preparing features and labels for ML models

---------------------------------------------------------------
4) SCIKIT-LEARN (sklearn)
---------------------------------------------------------------

TYPE:
- Local Python Machine Learning library

PURPOSE:
- Machine learning model development
- Model evaluation

WHY IT IS REQUIRED:
- Train Random Forest and XGBoost models
- Evaluate performance before spatial deployment

HOW IT IS USED:
- Model training
- Train-test split
- Accuracy, precision, recall, F1-score, AUC

IMPORTANT NOTE:
- Models trained here are used only for evaluation
- They cannot be directly used inside Earth Engine

---------------------------------------------------------------
5) MATPLOTLIB
---------------------------------------------------------------

TYPE:
- Local Python visualization library

PURPOSE:
- Plotting and visualization

WHY IT IS REQUIRED:
- Visual interpretation of results

HOW IT IS USED:
- Display predicted and true wildfire maps
- Visualize error maps (TP, TN, FP, FN)
- Save figures for reports and documentation

---------------------------------------------------------------
6) RASTERIO
---------------------------------------------------------------

TYPE:
- Local Python geospatial library

PURPOSE:
- Read and write raster (GeoTIFF) files

WHY IT IS REQUIRED:
- Output maps from Earth Engine are GeoTIFFs
- Raster-level validation is needed

HOW IT IS USED:
- Reading predicted wildfire rasters
- Reading ground truth rasters
- Pixel-wise raster comparison

---------------------------------------------------------------
7) FOLIUM
---------------------------------------------------------------

TYPE:
- Local Python mapping library

PURPOSE:
- Interactive map visualization

WHY IT IS REQUIRED:
- Quick visualization of study area and spatial extent

HOW IT IS USED:
- Display study area boundaries
- Visual map inspection during analysis

---------------------------------------------------------------
GOOGLE EARTH ENGINE AUTHENTICATION (DETAILED)
---------------------------------------------------------------

Google Earth Engine authentication for this project was completed using
the interactive token-based authorization method.

The authentication link generated by the Earth Engine API was opened in
a web browser. A Google account was selected, and the usage purpose was
chosen as "Personal / Academic Use", which provides free access.

A new Earth Engine project was then registered by assigning a project
name. After project creation, an authentication token was generated and
pasted into the authentication text box provided by the API interface.

This token securely authorizes the local Python environment to access
Google Earth Engine services. No billing or payment method is required.

---------------------------------------------------------------
WORKFLOW OVERVIEW
---------------------------------------------------------------

1) Study area definition using bounding box
2) Feature extraction (NDVI, EVI) from MODIS
3) Fire label generation using BurnDate
4) Balanced dataset creation
5) Model training and evaluation (Python)
6) Model retraining inside Earth Engine
7) Pixel-wise wildfire prediction
8) Raster export (GeoTIFF)
9) Spatial confusion matrix and metrics

---------------------------------------------------------------
OUTPUT FILES
---------------------------------------------------------------
WF_RF_PRED_BC_2023.tif        → Predicted wildfire map
WF_TRUE_BURN_BC_2023.tif     → Actual burned area (MODIS)
Error_Map_TP_TN_FP_FN.png    → Spatial confusion matrix

---------------------------------------------------------------
LIMITATIONS
---------------------------------------------------------------
- Only vegetation indices are used
- No weather or human activity data
- MODIS resolution may miss small fires

---------------------------------------------------------------
LICENSE
---------------------------------------------------------------
This project is intended for educational and research purposes only.

---------------------------------------------------------------
FINAL NOTE
---------------------------------------------------------------
This project clearly separates:
- Cloud-based geospatial processing (Google Earth Engine API)
- Local machine learning and validation (Python libraries)

This design enables scalable, explainable, and spatially validated
wildfire prediction.

