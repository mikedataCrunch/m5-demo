# M5 Demo

*Note: Most sections are taken from the AIM PHD in Data Science time series handbook (2021), specifically, the chapter on Winningest Methods done by Sebastian Ibañez and Michael Dorosan.*

Traditionally, ARIMA, VAR, and Exponential Smoothing methods are the go-to for time series forecasting. While the main advantage of traditional statistical methods is their ability to perform more sophisticated inference tasks directly (e.g. hypothesis testing on parameters, causality testing), they usually lack predictive power because of their rigid assumptions. That is not to say that they are necessarily inferior when it comes to forecasting, but rather they are typically used as performance benchmarks.

In this repository, we demonstrate the fundamental ideas and approaches used in the  recent Makridakis forecasting competition, M5, which began  

In M5, challengers from all over the world competed in building time series forecasting models for both accuracy and uncertainty prediction tasks specific to forecasting Walmart stores sales (event sponsor) across different product categories.



## Notebooks:

The repository contains the following notebooks:

* `hierarchical_forecasting.ipynb` - discusses some reconciliation techniques specific to hierarchical forecasting pursuits (e.g., M5 dataset).
* `sample_entry.ipynb` - shows a pipeline for an entry to the M5 competition. The notebook illustrates the machine learning approach--that is, tuning a LightGBM model in terms of `lookback` window, the use of exogenous variables, and an implementation of either a direct forecasting or regressor chain model training method.


## Mini-competition Structure

The repository is designed to facilitate a mini competition for M5. The following directories lends for the uses described below:

1. `README.md` - that briefly describes the competition, and data sources.
2. `Leaderboards Notebook` - each competition subdirectory provided with a leaderboards notebook to facilitate performance comparison.
2. `Entries` - this directory may contain the following:
    * `README.md` - (required) to provide a brief description of the entry as well as details on how to navigate through the files provided.
    * `Notebook` - (required) 1 or more notebook that supports the reported WRMSSE scores in the leaderboards section of the competition.
    * `trained_models` - (not required) included in .gitignore, this folder contains re-trained models on best paramters.
    * `predictions` - (not required) included in .gitignore, this folder contains the resulting predictions. 
    * `tuning` - (not required) included in .gitignore, this folder contains files used in tuning. Such as `.db` files for optuna experiments
    * `utils.py` (required) which contains functions that are useful for the specific competition.
    * `PATHS.py` (not required) which contains file paths used in the Notebooks.