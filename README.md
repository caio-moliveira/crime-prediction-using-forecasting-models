# Forecasting Crime Rates in Ireland Using Time-Series Models


### Caio Machado de Oliveira
### ID: 2020351


###  A Report Submitted in Partial Fulfilment of the requirements for the Degree of BSc in Computing in IT (4th year)



 

### May 2024



### Supervisor: Dr. Muhammad Iqbal




Declaration 
			
By submitting this assessment, I confirm that I have read the CCT policy on Academic Misconduct and understand the implications of submitting work that is not my own or does not appropriately reference material taken from a third party or other sources. I declare it to be my work and that all material from third parties has been appropriately referenced. I further confirm that this work has not previously been submitted for assessment by myself or someone else in CCT College Dublin or any other higher education institution.





























TABLE OF CONTENTS
ABSTRACT	4
1.	INTRODUCTION	5
Statement of Problem	5
Research Question	5
Data Acquisition	5
Limitations	6
2.	CRISP-DM	7
Methodology	7
Business Understanding	8
Data Understanding	9
Data Preparation	12
Modeling	13
Evaluation	16
Deployment	17
3.	CONCLUSIONS	18
REFERENCES	19













# ABSTRACT

This study aims to predict specific types of crimes in targeted areas across Ireland, employing a comprehensive dataset spanning several quarters, detailing the Guarda Division, type of offenses, and the number of crimes recorded. In response to the challenge of crime forecasting, which is pivotal for enhancing public safety and informing law enforcement strategies, we apply a selection of time series forecasting models known for their efficacy in crime prediction. These models include Prophet, ARIMA, SARIMA, and Holt-Winters Exponential Smoothing. Our analysis not only adapts these methodologies to handle the unique characteristics of crime data but also compares their performance to identify the most effective approach in predicting crime patterns based on RSME, MAE, and MAPE accuracy metrics. The results are expected to offer valuable insights into crime dynamics in Ireland, potentially guiding preventive measures and resource allocation. This paper will discuss the implementation of these models, the insights drawn from their comparative performance, and the implications for crime prevention and policy-making.






































# 1.	INTRODUCTION

## Statement of Problem

Criminality is a serious problem for any region, which risks its economy, security and quality of life. Crime is the biggest issue every nation is facing [1] and huge amount of money has been spent over the years to handle this issue [2]. There are numerous factors like poverty, large population, lack of resources etc. that drives criminal activities, and analysing crime based on all these factors is a challenge. Therefore, it’s critical to develop strategies for reducing crime. A city’s ability to grow economically is hampered by high crime rates. Law enforcement may greatly benefit from knowing the underlying factors that raise the risk of any given crime event happening at any given moment in order to avoid crime incidents.[3]
Statistics has become extremely important as it can help explain what has happened in the past, what is happening in the present, and what may happen in the future. A statistics textbook is filled with countless real-world examples [4]. Crime rate prediction uses statistics in machine learning models to build systems for finding future crime patterns and helping law enforcers solve crimes, ultimately reducing crime rates. Crime forecasting refers to the ability to predict future crimes, even years in advance, in order to increase crime prevention. This can be achieved using time series approaches to identify future crime trends from time series data.

## Research Question

I.	What is the predictive accuracy of various time series models (Prophet, ARIMA, SARIMA, Holt-Winters) when forecasting crime rates in Ireland?

II.	How do the forecasting models compare in terms of accuracy metrics (RMSE, MAE, MAPE) when predicting crime rates in Ireland?

III.	What challenges and limitations are encountered in predicting crime rates using statistical models, and how does the report address these?

IV.	What strategic insights for crime prevention and law enforcement are derived from the model predictions?


## Data Acquisition

The data required for this study was sourced from the Central Statistics Office's (CSO) official statistics portal, which is publicly accessible for scientific and academic purposes. The dataset includes a comprehensive range of columns such as STATISTIC Label, Quarter, Garda Division, and Type of Offence. The dataset contains crime incidents, which are systematically categorized under approximately 200 different types, such as theft, murder, assault, and burglary. This classification adheres to the Irish Crime Classification System (ICCS) [5]. The data set is captured and compiled through An Garda Síochána's PULSE (Police Using Leading Systems Effectively) system and detailed in the dataset from 2003 to 2023. This dataset is made available through the CSO Data Portal at CSO Crime Statistics.




## Limitations

I.	Data Collection Limitations: Crimes are recorded based on an officer’s determination that a criminal offense has likely occurred, which can introduce subjective biases into what is recorded and how it is classified.
II.	Statistical Methodology Limitations: The Machine Learning models assume a linear relationship between past and future values, which may not always hold in real-world data, especially in crime statistics that can be influenced by many unpredictable external factors.
III.	Date format Limitations: The fact that the data is ordered quarterly can influence the models in a different way, demanding a more tunned model. This can affect the accuracy of the model.
IV.	COVID-19 Limitations: Coronavirus have affected the entire world. There is no model that could ever predict this kind of phenomenon. Train a model using the data from that time will never work, so the decision of using data from before COVID-19 was made.



































# 2.	CRISP-DM

## Methodology

In order to develop a scalable and replicable Machine Learning model, aiming accurately forecast crimes in certain areas of Ireland, we followed the CRISP-DM (CRoss Industry Standard Process for Data Mining) model process. 
The CRISP-DM model was created to make large data mining projects, less costly, more reliable, more repeatable, more manageable, and faster [6]. This process consists of six iterative phases that goes from business understanding to deployment (see Figure 4.1).

Figure 4.1: CRISP-DM The data mining life cycle [7]: 



 
Figure 4.1 The data mining life cycle [7]

In this study, we will apply the CRISP-DM in our data mining project that yields a comprehensive understanding of crimes committed in Ireland, and making use of Machine learning models to forecast and predict these crimes in specific areas around Ireland. 
















Table 4.1: CRISP-DM process model description: 

 
 Table 4.1: CRISP-DM process model description

## Business Understanding

In the context of public safety in Ireland, the most important goal is to increase advanced analysis to predict and manage the rates more effectively. This involves understanding the strategic objectives of the local law enforcement as well as the operational requirements. It is a fact that crimes are connected to different influences such as economic status, unemployment, geographical, etc. This study aims to focus on deploying machine learning techniques to forecast specific types of crimes in targeted areas, enabling much more efficient allocation of police resources and proactive policing.
The business understanding phase plays a fundamental role identifying key questions such as the types of crimes most committed in central areas as shown in Figure 4.2 a graph line of the “Theft and related offences” crimes committed in the North Central Garda Division, which is a hotspot in Ireland.
 
Figure 4.2: 'Trend of "Theft and related offences" in D.M.R. North Central Garda Division'

The time series models provide an analytical backbone for understanding and predicting these crime trends [8], helping on data-driven decisions to prevent the increasing of crime and turning the country safer. By integrating these models, the project aligns technical solutions focusing on the predictive accuracy of each model being measured by the RMSE, MAE and MAPE of each of them, aiming for a positive impact on society safety.

## Data Understanding

The Data Understanding phase drives the focus to data sets that help to accomplish the project goals [9].
The details of how data was collected and organized is shown on Chapter 1 “Data Acquisition”.
In this study, we used Jupyter Notebook to analyse the data gathered and apply the machine learning models. 
The first step in this phase is describing the data to address the conditions and key characteristics of the table. For most modelling techniques, the amount of data is a fundamental key, as well as the value types (e.g. numerical, categorical, and Boolean).

Figure 4.3 enable the user to have this knowledge about the data. 

 

Figure 4.3: data.info() in Jupyter Notebook 

Furthermore, .describe() help us drawing important insights in the numerical features such as the amount of zero values in our data. As shown in Figure 4.4, the quantity of zero values is around 25% of our data. 

 

Figure 4.4:  data.describe()  in Jupyter Notebook 

In this study, the focus is in specific ‘Types of Offences’, as well as the regions, described by ‘Garda Division’. Using the .unique() give us a list of all the unique values in the feature.

  
Figure 4.5: Checking for unique values on ‘Garda Division’ column in Jupyter Notebook

 
Figure 4.2: 'Checking for unique values on ‘Type of offences’ column in Jupyter Notebook

To proceed effectively with our data mining project, we consider using the values with the biggest numbers, meaning the most committed crimes in both North and South in Dublin Metropolitan Region (D.M.R) as following the figures 4.6 and 4.7:

 
Figure 4.6: Plot from Jupyter Notebook: Top 5 most committed crimes in 'D.M.R. South Central Garda Division'

 
Figure 4.7: Plot from Jupyter Notebook: Top 5 most committed crimes in 'D.M.R. North Central Garda Division’

The second phase of the CRISP-DM methodology is critical for decision-making in the subsequent phases. The information gathered during this phase about the data will help in better preparing and is perhaps the most challenging and crucial step when applying machine learning models.

## Data Preparation

Once we narrow down the business problem and understood the data, we can now begin to prepare the data for analysis. Most of the data in real world is highly noisy, this means dealing with missing data, null values, duplicate values and outliers. 
The data preparation process is extensive and tends to take approximately 50-70% of the project time [9]. It covers all activities to construct the final dataset from the initial raw data.
During the data cleaning it was decided to implement the following approaches:

i.	Dropping not useful columns (e.g. "STATISTIC Label", "UNIT")
ii.	Renaming columns to minimize misspellings and easy to understand.
iii.	Replace missing values in the column ‘Crime’ by 0.
iv.	Turning the ‘Crime’ column data type from float64 to int64.
v.	Dropping all observations containing 0 values.
vi.	Removing the text “Garda Division” from each observation in “Garda Division” Column.

In this project, we are preparing the data for forecasting purposes, meaning that the column containing the ‘date’ must be in a date-time format in order to apply any time series model. At the end of the process, we made a modification to the date column by changing the format from "2003Q1" to "2003-01-01" to ensure its compatibility with time series models. Additionally, we set the date column as the index, as it is an essential requirement for time series analysis.
After all implementation, the data was reduced from 166.992 observations to 120.808 shown in Figure 4.8, as was expected due the amount of zero values containing in the dataset. 
	
 
Figure 4.8: data.info() & data.describe() after cleaning

Finally, after applying all the techniques presented earlier in this section, we have significantly improved the quality of our data. Below, in figure 4.9 is a preview of the first 10 observations, illustrating the effectiveness of the cleaning process applied. 	

 
Figure 4.9: First 10 observation of the cleaned dataset.

## Modeling

### Prophet 
The first forecasting model applied in this study is Facebook Prophet, which is based on an additive regression model [10]. This model only accepts the inputs from the columns Date and Crime. Later, the column Date was changed to ‘ds’ and the column count was updated to ‘y’ in accordance with the prophet model’s specifications[11]. As we are predicting quarterly crime data, the data frequency in use is represented by the acronym ‘QS’, which stands for "Quarterly Start." The crime dataset has now been split into training and testing. To fit the prophet model for training data, we use the .fit() function. Once trained, we employ the .predict() function to forecast the next 7 quarters. To compare the test and forecasted values, then evaluated the model according to the metrics chosen for this study. Figure 4.10 depicts the comparison of the train, test, and forecasted models in a plot.

 
Figure 4.10: Prophet Model Comparison

### ARIMA & SARIMA

The crime data is first put into a dataset by parsing the Date column and converting it to a Date Time format in Jupyter Notebook once the necessary libraries have been loaded. Only the Date and Crime columns are now used as input to the model. 
If the time series data is stationary or not, it is determined from the beginning. [12] The Dickey-Fuller test did not reject the null hypothesis, indicating that a unit root is present, meaning our training set is non-stationary. Furthermore, the differencing (value of d) was carried out followed by another Dickey-Fuller test, giving a p-value of less than 0.05, which demonstrates that the time series does not have a unit root and therefore is stationary [13].
The ACF and PACF plots, respectively, were used in determining which parameter should be supplied to the ARIMA and SARIMA model. However, this analysis is visual and might not be effective. In our study, we carried out two other tests to determine the best ARIMA and SARIMA parameters. First one, auto_arima from ‘pmdarima’ library, which uses different range of the AR (p), MA (q), differencing test (d), based information criteria (AIC and BIC), as well as parameters for the Seasonal ARIMA (P, D, Q) [14]. The second one is a for loop, where we select the range of each variable of the ARIMA and SARIMA models, and run tests on each possible combination within the range selected, then choose the best model based on the lower AIC value [15]. 
After run through these three types of analysis and perform tests for all results, we decided to use order = (7,2,4) for the ARIMA model, and (3, 1, 1) x (9, 1, 0, 4) for the Seasonal-ARIMA model.
Similar steps are followed to fit ARIMA [16] and SARIMA [17] model. The model is then fitted using the.fit() method. The values for the test data are predicted using the function .get.prediction().
After training the model, we plot a graph to compare its predictions with the original test set in order to evaluate how well the model predicts future steps as shown in the Figure 4.11 and 4.12:
 
Figure 4.11: ARIMA Model Comparison
	 
Figure 4.12: Seasonal ARIMA Model Comparison

### HOLT-WINTERS EXPONENTIAL SMOOTHING

This model is particularly effective for datasets with trends and seasonality. It assumes seasonal variation in crime rates over quarterly periods in our samples. The additive component for trend and seasonality is appropriate as the amplitude is independent of the average level of the series [18]. After running tests using both additive and multiplicative, the additive model gave better results.
The model is equally fitted to the training dataset in compared to the other models. The hyperparameters differ, as we have in TES [19], alpha, beta and gamma. The hyperparameters control the level, trend, and seasonal smoothing coefficients, respectively, and play a crucial role in our model responsiveness regarding to the changes in the data. In our model, a grid search was carried out to find the best hyperparameters based on the best Mean Absolute Error (MAE). Moreover, the comparison between the model being applied to the test against the original test data is shown in the Figure 4.13.

 
Figure 4.13: Triple Exponential Smoothing Model Comparison

## Evaluation

There exist several ways to measure the accuracy of the forecasting model. In this study we will are using Root Mean Squared Error (RMSE) and Mean Absolute Error (MAE), which evaluate the modelling capability as well as the predictive ability. The values obtained from test and forecast data are used to calculate these metrics [20].

Root Mean Square Error - RMSE 
A performance indicator called Root Mean Squared Error (RMSE) is used to calculate the standard deviation of errors. The performance of the model improves with decreasing RMSE values. 

Mean Absolute Error - MAE 
A performance indicator called mean absolute error (MAE) calculates the absolute average by adding the differences between the original and predicted values and dividing the result by the total number of rows. 

Mean Absolute Percentage Error - MAPE 
This indicator is the MAE measured in percentage.
	
The crime data analyzed in this study has a range from 2003-01-01 to 2019-10-01. We decided not use the values during COVID-19 as it was a global phenomenon that could never be predicted for any machine learning model. The training and test set was divided as follow:
Train set: 2003-01-01 : 2017-10-01 (60 values)
Test set: 2018-01-01 : 2019-10-01 (8 values)
Each of the following results are provided more detailed. The formalization of the projects assessment is presented in a table format meeting the business success criteria.

 
## Deployment

The deployment phase ins understood as the concrete actions based on the model trained. The focus of this study is on building and evaluating models to forecast specific crimes in certain areas in Ireland. The main deployment involves integrating the forecast model into the existing crime data management system utilized by An Garda Síochána. The PULSE system, which has been working on the crime incident data, would be an ideal platform for embedding these models, enabling more informed efficient public safety management and decision-making. 


























# 3.	CONCLUSIONS

The study explores into the CRISP-DM methodology for developing machine learning models for crime prediction, a topic of increasing interest, which become a hot research area due to its potential impact on society security. 
Numerous studies have employed various machine learning approaches for crime prediction, some of them with a focus on classification models and neural networking models such as the Recurrent Neural Network (RNN), that can be possibly considered for further study. 
The primary objective of the study was to identify the optimal forecasting model for crime prediction using real-world data. The study involved the utilization of four machine learning models - PROPHET, ARIMA, SARIMA, and TSE (Triple Exponential Smoothing) - applied to quarterly data from 2003 to 2019, focusing on the type of offense "Theft and related offenses" in the Dublin Metropolitan Region South Central Garda Division. The performance of the models was evaluated using RMSE, MAE, and MAPE metrics. After training and testing, it was determined that the SARIMA model exhibited the most accurate forecasting performance, achieving RMSE = 58.24, MAE = 42.91, MAPE = 2.05%. These findings have the potential to assist law enforcement agencies in decision-making.
































# REFERENCES

[1] Elyta, E., Mujiono, D. I. and Sagena, U. W. (2022). Facing the dangers in indonesia’s waters: Government’s efforts in proposing illegal, unreported and unregulated fishing as transnational organized crime, Intermestic: Journal of International Studies 6(2): 336– 352

[2] Laycock, G. (2013). Defining crime science, pp. 3–24.

[3] Calatayud, J., Jornet, M. & Mateu, J. Modeling noisy time-series data of crime with stochastic differential equations. Stoch Environ Res Risk Assess 37, 1053–1066 (2023). https://doi.org/10.1007/s00477-022-02334-8	

[4] Hyndman, R.J., & Athanasopoulos, G. (2018). Forecasting: principles and practice. Monash University, Australia.

[5] Guide to How Crime is Recorded and Counted by An Garda Síochána. (2020). Available at: https://www.garda.ie/en/about-us/publications/policy-documents/guide-to-how-crime-is-counted-and-recorded.pdf.

[6] Wirth, R., & Hipp, J. (2000). CRISP-DM: Towards a Standard Process Model for Data Mining.

[7] IBM (2021). CRISP-DM Help Overview. [online] www.ibm.com. Available at: https://www.ibm.com/docs/en/spss-modeler/SaaS?topic=dm-crisp-help-overview.

[8] Murphy, K.P. (2023). Probabilistic Machine Learning. MIT Press.

[9] www.ibm.com. (n.d.). Introduction to CRISP-DM. [online] Available at: https://www.ibm.com/docs/en/spss-modeler/SaaS?topic=guide-introduction-crisp-dm.

[10] Taylor, S.J. and Letham, B., 2017. Forecasting at Scale. 

[11] Prophet. (2022). Quick Start. [online] Available at: https://facebook.github.io/prophet/docs/quick_start.html#python-api.

[12] Ďurka, P. and Pastoreková, S., 2012. ARIMA vs. ARIMAX – Which approach is better to analyze and forecast macroeconomic time series?

[13] Brockwell, P.J. and Davis, R.A. (2016). Introduction to Time Series and Forecasting. Cham Springer International Publishing.

[14] alkaline-ml.com. (n.d.). pmdarima.arima.auto_arima — pmdarima 1.5.3 documentation. [online] Available at: https://alkaline-ml.com/pmdarima/modules/generated/pmdarima.arima.auto_arima.html.

[15] Zhang, Y. and Meng, G. (2023). Simulation of an Adaptive Model Based on AIC and BIC ARIMA Predictions. Journal of physics, 2449(1), pp.012027–012027. doi:https://doi.org/10.1088/1742-6596/2449/1/012027.

 [16] www.statsmodels.org. (n.d.). statsmodels.tsa.arima.model.ARIMA — statsmodels. [online] Available at: https://www.statsmodels.org/stable/generated/statsmodels.tsa.arima.model.ARIMA.html.
 
[17] www.statsmodels.org. (n.d.). statsmodels.tsa.statespace.sarimax.SARIMAX — statsmodels. [online] Available at: https://www.statsmodels.org/dev/generated/statsmodels.tsa.statespace.sarimax.SARIMAX.html.

[18] Kalekar, P.S., 2004. Time series forecasting using holt-winters exponential smoothing. Kanwal Rekhi school of information Technology.

[19] Statsmodels.org. (2014). statsmodels.tsa.holtwinters.ExponentialSmoothing — statsmodels. [online] Available at: https://www.statsmodels.org/dev/generated/statsmodels.tsa.holtwinters.ExponentialSmoothing.html.

[20] Chai, T. and Draxler, R.R. (2014). Root mean square error (RMSE) or mean absolute error (MAE)? – Arguments against avoiding RMSE in the literature. Geoscientific Model Development, 7(3), pp.1247–1250. doi:https://doi.org/10.5194/gmd-7-1247-2014.

