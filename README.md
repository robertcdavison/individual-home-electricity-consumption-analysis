# Energy Load Forecasting using Neural Networks and Household classification based on consumption patterns

### Executive Summary

A majority of homes in America have smart meters which track energy consumption and help provide a more accurate picture of the state of energy supply and demand. Electricity and energy companies will always benefit from more accurate demand forecasting and from gaining a better understanding of consumer behavior. This report seeks to apply various supervised and unsupervised models in order to analyze and understand household electricity consumption as well as to forecast demand. A kaggle dataset containing daily smart meter electricity consumption statistics for over 5,500 homes in London, England from 2012 to 2014 was used along with daily weather data. Each home was also given a preassigned economic classification, called an ACORN, which can be used for futher analysis and classification. 

This report is broken into two parts, classification and prediction. For classification, household electricity profiles were sorted into clusters with similar characteristics using k-means clustering, and PCA. For the prediction portion of this project, a handful of prediction models, including ARIMA and RNN, and LSTM neural networks, were used to forecast total daily energy consumption.

Link to Kaggle: https://www.kaggle.com/jeanmidev/smart-meters-in-london

---

### Models Used

#### Clustering
* K means
* PCA

#### Forecasting
* ARIMA
* RNN Neural Network
* LSTM Neural Network

---

### Primary Findings

First, the data were pivoted so that each house was an observation with 536 columns corresponding to the total amount of energy consumed that day. PCA was carried out on this dataset with the theory that the first few principle components would correspond to clusters of homes in similar ACORN. A plot of the first principle component vs. the second principal component, however, showed poor separation between ACORN groups. K-Means clustering was also carried out on the same data, but this time with 6 columns corresponding to the mean of the main energy metrics. This clustering also showed poor separation with a silhouette score of 0.38.

For the forecasting portion of the project, two different neural networks were applied to the multivariate consumption data. Each made predictions for the total daily electricity load for all homes based on 13 features aggregated features including median energy consumption, daily max temperature, and cloud cover to name a few. The training set consisted of 487 days and the testing set 55. The LSTM model achieved an RMSE of 2,367 (kWh), performing slightly worse than the RNN model which had an RMSE of 2,188 (kWh). The LSTM was able to predict the daily spikes or irregularities in consumption while the RNN model made more conservative predictions close to the mean. 

**Figure 1.** Total energy consumption forecasts aggregated for all homes in the dataset. **Left** LSTM Neural Network Forecast with an RMSE of 2,367 kWh. **Right** RNN forecast with an RMSE of 2,188 kWh


![](nn_forecast.png)

---

### Conclusions and Next Steps

This report set out to both classify homes based on their electricity consumption profiles and to apply neural networks to timeseries load forecasting. ACORNs showed a weak relationship with electricity consumption data. Only the wealthiest and poorest groups consumed a notably different amount of energy compared to the middle groups which all consumed similar amounts. While grouping homes into meaningful clusters proved difficult, timeseries forecasts exhibited better results. 

In an effort to give more meaningful load forecasts, more research should be done into using Bayesian Neural Networks or Gaussian processes because they provide built in confidence intervals. These confident intervals could provide useful insight into expected modeling error. Other next steps would be to iteratively add relevant features such as a column that tells whether the following day is a holiday or if bad weather is expected. 
