# M5 Demo

*Note: Most sections are taken from the AIM PHD in Data Science time series handbook (2021), specifically, the chapter on Winningest Methods done by Sebastian Ibañez and Michael Dorosan.*

Traditionally, ARIMA, VAR, and Exponential Smoothing methods are the go-to for time series forecasting. While the main advantage of traditional statistical methods is their ability to perform more sophisticated inference tasks directly (e.g. hypothesis testing on parameters, causality testing), they usually lack predictive power because of their rigid assumptions. That is not to say that they are necessarily inferior when it comes to forecasting, but rather they are typically used as performance benchmarks.

In this repository, we demonstrate the fundamental ideas and approaches used in the  recent Makridakis forecasting competition, M5, which began  

In M5, challengers from all over the world competed in building time series forecasting models for both accuracy and uncertainty prediction tasks specific to forecasting Walmart stores sales (event sponsor) across different product categories.

## Dataset

Dataset used here can be downloaded from [`Kaggle`](https://www.kaggle.com/c/m5-forecasting-accuracy). After download, save the `.csv` files into a directory named: `data/raw` within the cloned `m5-demo` repository. 

Alternatively, you can also find the data in this [`google drive link`](https://drive.google.com/drive/folders/1D6EWdVSaOtrP1LEFh1REjI3vej6iUS_4). 


## Notebooks:

The repository contains the following notebooks:

* `hierarchical_forecasting.ipynb` - discusses some reconciliation techniques specific to hierarchical forecasting pursuits (e.g., M5 dataset).
* `sample_entry.ipynb` - shows a pipeline for an entry to the M5 competition. The notebook illustrates the machine learning approach--that is, tuning a LightGBM model in terms of `lookback` window, the use of exogenous variables, and an implementation of either a direct forecasting or regressor chain model training method.


## Other Files:
* `utils.py` - which contains functions that are useful for the method employed in `sample_entry.ipynb`
* `PATHS.py` - which contains file paths used in the notebooks.


## M5 Mechanics

### Metrics and Evaluation : *Begin with the end in mind*
As with the original M5 competition, the objective is to minimize the forecasting error--measured by the Weighted Root Mean-Squared Scaled Error (RMSSE). This metric scales the usual root mean-squared error and aggregates the forecasting error of all the 42,840 forecasts (1 per series) in a weighted manner. These weights are provided by the `M5 Competition` and are based on the Dollar amount of sales for each of the 42,840 series. *Care must be taken into account in evaluating the results due to differences in `weights_evaluation.csv` and `weights_validation.csv`--differences are due to live updating of the proportion dollar amount of sales in the days that followed*. The former SHOULD be used in evaluating the final (entry) forecasts' WRMSSE while the latter for tuning the model--for entries that use WRMSSE as a tuning objective (Accuracy competition).

WRMSEE formula:


![equation](https://latex.codecogs.com/png.image?%5Cdpi%7B80%7D%20%5Cbg_white%20%5Cinline%20%5Ctext%7BWRMSSE%7D%20=%20%5CSigma_%7Bi=1%7D%5E%7B42,840%7D%20w_i%20*%20%5Ctext%7BRMSSE%7D%20)
          
*Honor Code: Unlike the original M5 competition, the evaluation set (last 28-day actual data) is already made available to entrants--mainly because M5 is already finished. While it is tempting to fit forecasting performance to the actual evaluation set, DO NOT, as this defeats the purpose of the competition.*

## References
For more information on the competition mechanics see: https://github.com/Mcompetitions/M5-methods/blob/master/M5-Competitors-Guide.pdf

Additionally, winningest methods for M5 are dicussed in the same repository: https://github.com/Mcompetitions/M5-methods