# Article

Building Accurate Models for Unit Sales Prediction in Favorita Stores using Time Series Forecasting
Introduction:

Time series data is a sequence of data points that are indexed and ordered chronologically over time. Time series forecasting is a statistical technique used to make predictions about the future values of a variable based on its past behavior.

Favorita Corporation is an Ecuadorian company that creates and invests in commercial, industrial, and real estate areas. This project aims to forecast unit sales of products across different stores to optimize inventory management, marketing strategies, and pricing decisions. The company will adopt this model to help Favorita Corporation make insightful decisions in relation to its retail sales, promotions, and customer satisfaction.

In this article, I will discuss the significant procedures used in building accurate models for sales prediction in Favorita stores using time series forecasting.

Let’s get started!

Hypothesis
Null Hypothesis: Promotional activities have a significant impact on store sales at Corporation Favorita.
Alternate Hypothesis: Promotional activities do not have a significant impact on store sales at Corporation Favorita.
Click on the links below for more information on the libraries that were imported,

Numpy: https://numpy.org/doc/stable/user/absolute_beginners.html.
Pandas: https://www.educative.io/answers/what-is-pandas-in-python.
Matplotlib.pyplot: How to Install Matplotlib in Python? — Scaler Topicshttps://www.scaler.com › topics › install-matplotlib
Seaborn : https://seaborn.pydata.org/index.html
Scikit-learn : https://scikit-learn.org/stable/
https://plotly.com/python/

I conducted a thorough overview of the dataset. This revealed that all the datasets used in the project did not lack any missing values, with the exception of oil_data. 43 entries in the oil_data’s dcoilwtico column were missing. The method = ‘bfill’ was used to fill in the missing values. The exploration data analysis and univariate analysis that I performed on the datasets yielded some interesting results that enabled me to have a better understanding of the datasets.

I did a thorough overview of the dataset. With the exception of oil_data, this revealed that none of the datasets utilized in the project had any missing values. The dcoilwtico column in oil_data was missing 43 entries. To fill in the missing values, method = ‘bfill’ was utilized due to the sequential nature of the figures. The exploratory data analysis and univariate analysis that I ran on the datasets gave some intriguing insights that helped me understand the datasets better.

There are 16 distinct states, with Pichincha having the most stores. There are 22 distinct cities, with Quito having the most. There are 16 different states altogether, with Pichincha having the most stores. With 22 distinct cities, Quito has the largest number. There are 5 different store kinds, with store D having the most of them. After exploring the store_data dataset, no outliers were discovered but some outliers were observed in the transactions_data. The values 0.0412413665900577 and 1.518351 indicate that the ‘cluster’ and transaction columns have a slightly positive skew, indicating that the distribution’s tail is slightly longer on the right side. However, the fact that the value is close to zero suggests that the distribution is almost symmetrical.

Exploring the Holiday Dataset

From the image captured below, the holiday has the highest size of 221 counts, and the work day and bridge both have the smallest sizes of 5 counts, respectively. Except for 12 holidays, the majority of the holidays were national and were not transferred.

Exploring the oil dataset

According to the data presented above, there has been a downward or declining trend over time. There are no anomalies. In conclusion, oil prices have been declining over time.

Exploring the family dataset

All of the families had the same count, which makes sense because the product’s family was still included on days when no purchases were made. From January to May of 2015, promotions were scaled back.
They raised their promotions for May 2016, which I assume is due to the earthquake. In addition, we can detect an upsurge in marketing from March to July of 2017.

From January to May of 2015, promotions were scaled back.
They raised their promos for May of 2016, which I assume is due to the earthquake. In addition, we can detect an upsurge in marketing from March to July of 2017.

Bivariate & Multivariate Analysis

Multivariate analysis refers to statistical techniques used to analyze data with multiple variables or features. In other words, it is an extension of univariate analysis (analysis of a single variable) and bivariate analysis (analysis of two variables) to analyze and understand the relationship between more than two variables simultaneously.

Resourceful links for Bivariate & Multivariate Analysis

Multivariate analysis: https://en.wikipedia.org/wiki/Multivariate_analysis
Bivariate analysis: https://en.wikipedia.org/wiki/Bivariate_analysis
Multivariate statistics: https://en.wikipedia.org/wiki/Multivariate_statistics
Bivariate statistics: https://en.wikipedia.org/wiki/Bivariate_statistics
Multivariate analysis in Python: https://towardsdatascience.com/multivariate-data-analysis-in-python-an-introduction-to-principal-components-analysis-pca-2a8ccbcbb15e
Bivariate analysis in Python: https://towardsdatascience.com/bivariate-analysis-with-python-ffb09b8cbb0b

Let’s look at how the earthquake impacted transactions.

The visualizations below indicate that there was a significant increase in transactions the week after the earthquake on April 16, 2016, The crisis prevented people from the affected zone from moving around freely. Following the tragic event, people resumed their normal activities. Promotions in 2016 were quite consistent in April. They increased promotion at the end of April and the beginning of May of 2016. From April 29th to May 31st, 2016, a massive promotion was held.

Time Series Analysis:
Before developing a model, it is critical to comprehend the time series data and identify any trends, and seasonality. This can be accomplished by visually inspecting the data with tools such as line charts, histograms, and autocorrelation plots. The autocorrelation plot depicts the relationship between the time series data and its lag values, which can aid in determining the lag order for the ARIMA model.

Model Selection :
ARIMA, SARIMA, Prophet, and LSTM are some time series models that can be used to predict sales. The model chosen is determined by the nature of the data and the level of precision required. In this situation, I will work on different models compare the results, and decide the model that best suits the project.

Univariate Modelling

The goal of this type of modeling is to forecast the general sales for Favorita irrespective of the product type, store number, and other exogenous effects. Therefore, I will be using only time and the previous sales values to forecast the sales. Due to the large number of data points, it is difficult to discern any changes (trends and seasonality). -I observed some sharp dips at the start of each year. I will resample the data to a weekly frequency to help observe the shape of the data more clearly.

Univariate Statistical Modeling
The Augmented Dickey-Fuller (ADF) test is commonly used in time series analysis to test for the presence of a unit root, which indicates the presence of a trend in the data. The ADF test result showed that the p-value is more than 0.05, indicating that the result is not statistically significant. This means our data is non-stationary.

Parameter Estimation :
There are three parameters in the ARIMA model: p, d, and q. The order of the autoregressive term is represented by the p parameter, the degree of differencing is represented by the d parameter, and the order of the moving average term is represented by the q parameter. Methods such as the Akaike Information Criterion (AIC) or the Bayesian Information Criterion (BIC) can be used to estimate the parameters. Given that the dataset was non-stationary, I decomposed it to break down the time series into its individual components such as trend, seasonal, and residual.

The image above indicates that the were many significant spikes above the significant threshold that aren’t declining/decaying. This influenced my decision of using a moving average model. There is also some seasonality present in the image.

Model fitting and validation:
The ARIMA model can be fitted to the training data after the parameters have been estimated. The model’s correctness can be tested using testing data and metrics such as Mean Absolute Percentage Error (MAPE) or Root Mean Square Error (RMSE). From the diagrams below the model performed very well. The model can be fine-tuned by modifying the parameters and re-fitting it until it achieves the required level of accuracy. For instance, I use log transformation to improve the model instead I would examine other time models and improve the performance in my multivariate analysis.

Forecasting :
Once the model has been fitted and validated, it can be used to forecast future sales. To evaluate the model’s accuracy, plot the anticipated values versus the actual values. The goal here is to determine how the other columns (exogenous variables) influence sales and increase the accuracy of our models.

Workflow:

Datasets will be reviewed again.
Time series datasets will be merged for multivariate analysis.
Preliminary feature selection using Granger’s causality test.
I will use feature engineering to create a product.
Models with in-built feature selection can be used example decision trees.
Models used include:
SARIMAX
Facebook Prophet
VAR
Decision Tree
XGBOOST

The datasets to be used after the overview includes the transaction, oil, train, and holidays. I filtered other datasets to match the date of our train dataset(2013–01–01 to 2017–08–15) to forecast unit sales across all stores of Favorita. I noticed some missing rows in the holiday dataset will be replaced with “No holiday”, and transferred with “false” and missing rows in dcoilwtico will be filled using the “bfill “ function.

Feature selection using the Granger causality test

The Granger causality test is a statistical hypothesis test to determine whether one-time series is helpful in forecasting another. Since the aim is to make the model as accurate as possible I will use the Granger causality test. The null hypothesis will be rejected if the test results in the p-value > 0.05, otherwise, it is rejected. The test will be run over 20 lags to help make a well-informed judgment. Let's assume the holiday has an effect on sales.

I encoded the transferred column by first replacing the string “False” with the boolean and then later replacing the false with 0 and true with 1.
Multivariate modeling

This section will involve the comparison of one statistical model with two machine-learning models. The models will be developed using ; Facebook Prophet, SARIMAX, and decision tree. Assumption: In order to create our forecast, we must first obtain the future values for our exogenous attributes. Because the features are numerous, this can be a time-consuming task; therefore, we will use the previous values of the exogenous variables in our test data to forecast.

Prove of Hypothesis; The outcome of our Granger test indicates that, the p-value is greater than 0.05 which proves to accept my null hypothesis; Promotional activities have a significant impact on store sales at Corporation Favorita.

In conclusion, the models are ranked from best to worst, with the best-performing model at the top (index 2) and the poorest-performing model at the bottom (index 4).

With an MAE of 8.08 and an RMSLE of 0.107, the SARIMAX model (index 2) performed the best. With an MAE of 8.77 and an RMSLE of 0.109, the SARIMA model (index 5) also fared well. The Decision Tree model (index 1) performed slightly worse than the SARIMA models, with an MAE of 8.06 and an RMSLE of 0.128. With an MAE of 9.86 and an RMSLE of 0.234, the Facebook Prophet with exogenous variables (index 3) performed worse than the other models. The Random Forest model (index 0) has the highest MAE of 16.42 and the lowest RMSLE of 0.271, indicating that it is the least accurate of the models tested.

In summary, based on the metrics provided, the SARIMAX model performed the best, while the Random Forest model performed the poorest. The Facebook Prophet with exogenous variables (index 3) performed worse than the other models, with an MAE of 9.86 and an RMSLE of 0.234. The Random Forest model (index 0) had the highest MAE of 16.42 and an RMSLE of 0.271, indicating it is the least accurate among the models evaluated.

In summary, based on the given metrics, the SARIMAX model was the best-performing model, while the Random Forest model was the worst.

1







