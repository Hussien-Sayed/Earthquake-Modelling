# Earthquake Modeling
This repository is an extension to the work done here: https://github.com/NicolasSalgado/Earthquake_moon_project/tree/master by Peter Haney and Nicolas Salgado.

We first clarify that the previous analysis had a bad confusion that lead to a misleading conclusion. Then we apply multiple experiments to statistically distinguish magnitudes of earthquakes based on lunar and solar features.

## Data Preparation
In this analysis we further extend the data by introducing synthetic data where earthquakes didn’t have a record by our data source (of all magnitudes less than 4.8). We extend the merged dataset such that we have a single record for each (day-location cluster) (where location clusters are k-means clusters of longitude and latitude features). So for each day we should have k location clusters and for each we have a single record of the earthquake value. If the earthquake value / values were found as original records we consider the mean of their value in our new extended data, otherwise, we consider a median value (which is 2.4) for any missing record. For the synthetic no earthquake records, location values are picked as random values within the record cluster. By doing that we have a dataset that we can apply analysis to, and we can have a fair comparison between earthquakes which are bigger than 4.8 and which are less than 4.8. 

## Confusion clarification
Lunar illumination cycle is a little tricky to be interpreted, especially when one wants to tie illumination distribution across a lunar month to something else. The distribution of moon illumination across the lunar month is not uniform. Instead, the illumination periods of new moon and full moon are long relative to other periods. If we check the distribution of the illumination for these 2 cases in our new extended data, we notice no difference in the illumination distribution.
![distribution_ill_comp](https://github.com/user-attachments/assets/b1ee372d-c173-40a3-9a58-44128462076a)

## Experiments
We apply 5 types of ML models on our data which are the following:
- Transformer model (Regression)
- LGMB (Regression)

- FFNN (Classification)
- LGMB (Classification)
- LGMB with lags (Classification)

For regression models, the objective is to predict the magnitude of the earthquake value, while for classification, objective is to predict either magnitude is larger than 4.8 or not. For regression MAE is used as an evaluation metric, and for classification, accuracy is used.

## Results
The following results show that most of the experiments fail to beat the baseline score. However, the LGBM lag experiment was able to beat the baseline by a small value. We further check the significance of this small value using McNemar's test and we show that the small improvement in accuracy is significant.

### Transformer model (Regression)

### LGMB (Regression)

### FFNN (Classification)

### LGMB (Classification)

### LGMB with lags (Classification)

