# Lake Powell Delta Land Cover Classification

CNN-based land cover classification of Landsat imagery at the Colorado River 
confluence with Lake Powell, Utah (2013–2026).

Developed for GEOG 6160: Spatial Data Science, University of Utah.

## Overview

Classifies multispectral Landsat imagery into four land cover classes — Lake, 
River, Sediment Bank, and Rock — to track Colorado River delta exposure across 
14 years of reservoir level fluctuation. The Sediment Bank class serves as a 
proxy for delta position, supporting geology research into delta response to 
Lake Powell water levels and upstream sediment supply.

## Repository Structure

```
├── PrepData.ipynb               # Clip raw Landsat scenes and compute NDVI/NDWI
├── LandCoverExtractChips.ipynb  # Extract training chips from polygons
├── LandCoverCNN.ipynb           # Train and evaluate the CNN classifier
├── LandCoverPredict.ipynb       # Apply model to all 14 years
├── DeltaExtractChips.ipynb      # (Archived) Binary delta detection attempt
├── DeltaCNN.ipynb               # (Archived) Binary delta detection attempt
├── DeltaPredict.ipynb           # (Archived) Binary delta detection attempt
├── experiment_config.json       # Shared settings between notebooks
└── experiment_log.json          # Hyperparameter experiment results
```

## Requirements

Python 3.11, TensorFlow/Keras, rasterio, geopandas, numpy, scikit-learn, 
matplotlib, seaborn. Run in the `6160FinalEnv_PY311` conda environment on CHPC 
or equivalent.

## Usage

Run notebooks in order:

1. `PrepData` — clip raw Landsat scenes to study area and compute NDVI/NDWI
2. `LandCoverExtractChips` — set chip size and coverage threshold here, extract training chips
3. `LandCoverCNN` — train and evaluate the classifier; set augmentation toggle here
4. `LandCoverPredict` — apply trained model to all 14 years

Key settings (chip size, coverage threshold) are configured in `LandCoverExtractChips` 
and automatically passed to downstream notebooks via `experiment_config.json`.

## Notes

The Delta notebooks are retained for documentation purposes but did not produce 
usable results — see paper for explanation.
