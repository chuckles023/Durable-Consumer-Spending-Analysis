# Post Pandemic Durable Consumer Spending Analysis


November 29 2024

This analysis examines the unique shifts in consumer behavior during and after the pandemic, particularly how stimulus checks influenced spending on durable goods. Findings highlight the rapid rebound of goods spending compared to services and the depletion of pandemic-era excess savings. Using advanced econometric models, this report forecasts consumer spending on durable goods through 2029, providing actionable insights for strategic investments in a recovering economy.

Durable goods play an important role in forecasting demand and understanding consumer behavior.  Durable goods are physical products with longer life spans and are associated with significant investment and infrequent purchase cycles.  They are very sensitive to economic conditions, making them a good indicator of consumer confidence.  As the economy recovers from the Covid-19 downturn, understanding how durable goods will perform over the next 5 years can be important to inventory decision making, helping businesses align supply with shifting customer demand.  

An important aspect of the pandemic and ensuing economic downturn was the effect of the stimulus checks on savings held by consumers.  Higher consumer savings often lead to increased demand for durable goods, as individuals feel more financially secure and are willing to make significant purchases.  Understanding when these savings will be depleted and how this will influence consumption will help contextualize our forecasts.  

In January 2021, the FED released a report discussing demand during the pandemic.  They found that during most recessions, household spending on goods and housing tends to fall and services spending tends to respond weakly to the business cycle.  Surprisingly, the opposite was true during the pandemic, where services spending remained weak for multiple quarters while goods spending and housing investment were able to rebound and rise above pre-pandemic levels rather quickly.  One main reason for this observation was the role of social distancing in how consumers were behaving during the recession.  

According to the FED, two metrics for housing activity, new construction and home sales, saw an initial drop at the start of the pandemic but recovered quickly and rose above pre-pandemic levels.  A combination of different factors led to the resilience in the market.  Record low mortgage rates and the availability of online or limited contact tools for home buying encouraged activity.  New homebuyers were also more likely to have relatively high income, a sect of employees which experienced less unemployment comparatively.  These higher income households make up most of the effect in the rebound of housing activity as existing home sale growth is far greater in sales of $500,000+ compared to lower prices.  Ultimately, the characteristics of the pandemic changed people’s relationships with their home, maintaining and strengthening the market.  

Despite restrictions on leaving home, spending from CARES Act stimulus checks resembled pre-pandemic patterns, with a notable increase in goods spending following the payout of stimulus checks, especially online. While spending on durable goods initially fell below pre-COVID levels, it eventually surpassed expectations by the end of 2020\.  The effects of the shutdown caused consumers to shift from using their disposable income to purchase services towards a focus on the purchase of goods.  The pandemic made it much harder to eat out and travel.  Now in a post pandemic era, we are seeing a reversion of this trend.  Two years before the pandemic, personal consumption of durable and nondurable goods was at 31%, increasing to 36% in March and April of 2021\.  After the vaccine was released, we saw a decrease back down to 34% in December 2021\.  Consumer spending became strained due to supply chain constraints, rising prices from inflation, and diminishing government stimulus funds.  Travel and dining also saw an increase as people became more comfortable going out and social distancing measures were withdrawn.  

A study in early 2023 by Abdelrahman and Oliveira examined Pandemic Era excess savings which are defined as the difference between actual savings and the pre-pandemic trend.  What they found was that a combination of fiscal support from the government and a drop in household spending caused household savings to see a rise in the overall US economy, well above the pre-pandemic trend line.  When economic activity began to recover after the lockdown, households used these savings to support their new spending.  By the end of 2021 these savings had started to dry up, dipping below the pre pandemic trend.  

Abdelrahman and Oliveira determined that by March 2023, only $500 billion of the $2.1 Trillion in pandemic savings in the economy remained. Data revisions released by the Bureau of Economic Analysis after their initial study showed that household spending increased and household disposable income decreased in the last quarter of 2022 and the 1st quarter of 2023\.  They also found that consumer spending continued to grow going into the 2nd quarter.  Their new estimates would have aggregate excess savings all the way down to $190 billion by June and all the way gone by the 3rd quarter of 2023\.  Since its peak in August 2021, personal savings has been below pre-pandemic trend.  Compared to other recessions, aggregate excess savings performed in a completely different manner, peaking around 12 to 18 months and tapering off by 36\.  In other recessions like 2008, 2001, or 1980, aggregate excess savings slowly recovered over the course of a few years in a steady and predictable fashion.  

## Method:


To predict the growth of consumer spending over the next 5 years, we will use the metric PCEDG which measures personal consumption expenditures on durable goods.  We will create 2 competing models, one with a deterministic trend and one with a stochastic trend and forecast PCEDG. They will be trained on the PCEDG time series dating up to the 2008 financial crisis.  Then we will use the Granger Newbold test to determine which model is more accurate and use that model to forecast PCEDG over the next 5 years.  



## Econometric Analysis:

<p align="center">
  <img src="https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi31.png" width="70%">
</p>

 
**A graph of PCEDG (1984 \- Present)**  
**Unit: Billions of Dollars**  
**Frequency: Monthly**

## Modeling Personal Consumption using a Deterministic Trend ARMA (3,3):

```
 Box-Jenkins - Estimation by LS Gauss-Newton
NO CONVERGENCE IN 100 ITERATIONS
LAST CRITERION WAS  0.0003008
TRY INCREASING ITERS OPTION

Dependent Variable LPCE
Monthly Data From 1984:01 To 2009:01
Usable Observations                       301
Degrees of Freedom                        293
Centered R^2                        0.9957698
R-Bar^2                             0.9956688
Uncentered R^2                      0.9999853
Mean of Dependent Variable       6.5286337876
Std Error of Dependent Variable  0.3860471760
Standard Error of Estimate       0.0254065885
Sum of Squared Residuals         0.1891299579
Log Likelihood                       682.4504
Durbin-Watson Statistic                2.0590
Q(36-6)                               24.9151
Significance Level of Q             0.7291489

    Variable                        Coeff      Std Error      T-Stat      Signif
************************************************************************************
1.  CONSTANT                        177.67946  11378.06246      0.01562  0.98755139
2.  AR{1}                             0.89998      0.42986      2.09365  0.03715081
3.  AR{2}                            -0.13693      0.45329     -0.30208  0.76280702
4.  AR{3}                             0.23639      0.36665      0.64474  0.51960104
5.  MA{1}                            -0.31526      0.43410     -0.72623  0.46827769
6.  MA{2}                             0.07209      0.35221      0.20467  0.83797417
7.  MA{3}                             0.00796      0.19433      0.04095  0.96736128
8.  TREND                            -0.04522      1.90340     -0.02376  0.98106099

Inverse Roots of AR and MA polynomials
Absolute Value of MA Roots
1   0.077592
2   0.320262
3   0.320262

Absolute Value of AR Roots
1   0.486304
2   0.486304
3   0.999587

```

<p align="center">
  <img src = "https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi32.png" width="45%">
  <img src = "https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi33.png" width="45%">
</p>

The deterministic trend ARMA (3,3) model for the log of personal consumption expenditures (LPCE) demonstrates a strong overall fit, with an R2R2 of 0.9958. However, individual parameter significance is mixed:

* Trend Term: The coefficient (-0.04522) is not statistically significant (p=0.981p=0.981). 
* AR(1): Statistically significant (p=0.037p=0.037), indicating a relationship between current and previous periods.
* Other AR/MA Terms: Generally not significant, suggesting potential overfitting or issues in capturing underlying data dynamics. Despite high R2R2, the lack of significant coefficients raises concerns about the model's predictive power and robustness.

<p align="center">
  <img src="https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi34.png" width="70%">
</p>
```
Forecast Analysis for PCEFOR
From 2009:02 to 2014:12
Mean Error                 -0.0887747
Mean Absolute Error         0.0936523
Root Mean Square Error      0.1139442
Mean Square Error            0.012983
Theil's U                  153.145408

Mean Pct Error              -0.012800
Mean Abs Pct Error           0.013504
Root Mean Square Pct Error   0.016431
Theil's Relative U         153.980148

Theil Inequality Measure     0.008164
  Bias                       0.607007
  Variance                   0.372274
  Covariance                 0.020719
```

Forecast analysis reveals:

* Mean Absolute Error (MAE): 0.0937, indicating the model's average forecast error is small relative to the scale of LPCE.  
* Root Mean Square Error (RMSE): 0.1139, slightly larger, suggesting occasional larger deviations.  
* Theil's U (153.15): Very high, indicating poor relative performance compared to naive forecasting methods. While the deterministic trend model captures overall trends, its high forecast error variance and poor comparative performance suggest limited accuracy for long-term forecasting.

 

## Modeling Personal Consumption Expenditures using a Stochastic Trend ARIMA (1,1,3):

'''
Box-Jenkins - Estimation by LS Gauss-Newton
Convergence in    42 Iterations. Final criterion was  0.0000071 <=  0.0000100

Dependent Variable LPCE, differenced 1 times
Monthly Data From 1984:01 To 2009:01
Usable Observations                       301
Degrees of Freedom                        296
Centered R^2                        0.9956981
R-Bar^2                             0.9956399
Uncentered R^2                      0.9999851
Mean of Dependent Variable       6.5286337876
Std Error of Dependent Variable  0.3860471760
Standard Error of Estimate       0.0254910500
Sum of Squared Residuals         0.1923389145
Log Likelihood                       679.9183
Durbin-Watson Statistic                1.9915
Q(36-4)                               23.8464
Significance Level of Q             0.8499215

    Variable                        Coeff      Std Error      T-Stat      Signif
************************************************************************************
1.  CONSTANT                      0.003639446  0.000864197      4.21136  0.00003372
2.  AR{1}                         0.464862437  0.233597543      1.99001  0.04750909
3.  MA{1}                        -0.897620343  0.235492944     -3.81167  0.00016793
4.  MA{2}                         0.062120168  0.130665772      0.47541  0.63484348
5.  MA{3}                         0.147139486  0.060113638      2.44769  0.01495840

Inverse Roots of AR and MA polynomials

Absolute Value of MA Roots
1   0.322716
2   0.675235
3   0.675235

Absolute Value of AR Roots
1   0.464862
2   1.000000

'''

<p align="center">
  <img src = "https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi35.png" width="45%">
  <img src = "https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi36.png" width="45%">
</p>

The stochastic trend ARIMA (1,1,3) model for LPCE exhibits:

* Significant Parameters: The constant (p=0.000p=0.000), AR(1) (p=0.048p=0.048), and MA(3) (p=0.015p=0.015) are statistically significant, supporting the inclusion of these terms. 
* Good Fit: R2=0.9957R2=0.9957, comparable to the deterministic model, but with fewer parameters.  
* Stationarity Achieved: Differencing effectively removed the stochastic trend. This model is more parsimonious and statistically valid, suggesting it better captures the dynamics of LPCE.

 
<p align="center">
  <img src="https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi37.png" width="70%">
</p>
```
Forecast Analysis for PCEFOR2
From 2009:02 to 2014:12
Mean Error                 0.02069965
Mean Absolute Error        0.02227465
Root Mean Square Error     0.02517930
Mean Square Error            0.000634
Theil's U                    7.002004

Mean Pct Error               0.002937
Mean Abs Pct Error           0.003164
Root Mean Square Pct Error   0.003579
Theil's Relative U           7.045567

Theil Inequality Measure     0.001790
  Bias                       0.675832
  Variance                   0.000000
  Covariance                 0.324168
```

Forecast analysis for ARIMA (1,1,3) indicates:

* Lower Forecast Errors: MAE of 0.0223 and RMSE of 0.0252, much smaller than the deterministic trend model.  
* Theil's U (7.00): Drastically lower, showing better forecasting accuracy relative to naive methods. This model's reduced errors and superior performance metrics suggest it is the better choice for forecasting LPCE.

 

## Model Comparisons:
<p align="center">
  <img src="https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi38.png" width="70%">
</p>

**Granger-Newbold Test:**

Granger-Newbold Forecast Comparison Test  
Forecasts of LPCE over 2009:02 to 2014:12

Forecast Test Stat P(GN\>x)  
PCEFOR     20.1132 0.00000  
PCEFOR2   \-20.1132 1.00000

<p align="center">
  <img src = "https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi39.png" width="45%">
  <img src = "https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi310.png" width="45%">
</p>

'''
Correlations of PCEFOR Errors
Monthly Data From 2009:02 To 2014:12

Lag     ACF        PACF
   1   0.970391   0.970391
   2   0.954876   0.226546
   3   0.947539   0.199033
   4   0.934967  -0.005741
   5   0.920045  -0.046836
   6   0.904972  -0.054346
   7   0.896462   0.088038
   8   0.872603  -0.236849

Ljung-Box Q-Statistics
Lags  Statistic Signif Lvl
   1     69.723   0.000000
   2    138.213   0.000000
   3    206.646   0.000000
   4    274.270   0.000000
   5    340.744   0.000000
   6    406.048   0.000000
   7    471.131   0.000000
   8    533.774   0.000000

Correlations of PCEFOR2 Errors
Monthly Data From 2009:02 To 2014:12

Lag     ACF        PACF
   1    0.32363    0.32363
   2    0.05188   -0.05904
   3    0.03070    0.03589
   4   -0.07522   -0.10519
   5   -0.19145   -0.15039
   6   -0.23875   -0.15164
   7   -0.08414    0.04367
   8   -0.19210   -0.20994

Ljung-Box Q-Statistics
Lags  Statistic Signif Lvl
   1      7.755   0.005357
   2      7.957   0.018713
   3      8.029   0.045419
   4      8.467   0.075908
   5     11.345   0.044953
   6     15.890   0.014355
   7     16.464   0.021201
   8     19.500   0.012403

```
```
Diebold-Mariano Forecast Comparison Test  
Forecasts of PCEDG over 2009:02 to 2014:12  
Test Statistics Corrected for Serial Correlation of 6 lags  
Forecast    MSE     Test Stat P(DM\>x)  
PCEXP    16169.1851    2.8794 0.00199  
PCEXP2     806.9966   \-2.8794 0.99801
```
Granger-Newbold Test:
A test statistic of 20.1132 for the deterministic model and \-20.1132 for the stochastic model confirms significant differences in forecasting accuracy. The stochastic trend model is superior, as its errors exhibit lower autocorrelation and variance.

Diebold-Mariano Test:
The stochastic model (MSE \= 807\) significantly outperforms the deterministic model (MSE \= 16169), with a pp-value of 0.002 favoring the stochastic trend model. Conclusion: The stochastic trend ARIMA model is the more accurate and reliable choice for forecasting.

## Forecasting 2024-2029 using the ARIMA Model:

### Model:
```
Box-Jenkins - Estimation by LS Gauss-Newton
Convergence in    18 Iterations. Final criterion was  0.0000059 <=  0.0000100

Dependent Variable LPCE, differenced 1 times
Monthly Data From 1984:01 To 2024:10
Usable Observations                       490
Degrees of Freedom                        485
Centered R^2                        0.9969376
R-Bar^2                             0.9969123
Uncentered R^2                      0.9999839
Mean of Dependent Variable       6.8148112637
Std Error of Dependent Variable  0.4961822306
Standard Error of Estimate       0.0275712126
Sum of Squared Residuals         0.3686833052
Log Likelihood                      1066.8147
Durbin-Watson Statistic                1.9965
Q(36-4)                               31.8843
Significance Level of Q             0.4724967

    Variable                        Coeff      Std Error      T-Stat      Signif
************************************************************************************
1.  CONSTANT                      0.003844793  0.000683903      5.62184  0.00000003
2.  AR{1}                         0.290354553  0.484454476      0.59934  0.54922383
3.  MA{1}                        -0.556794226  0.485359352     -1.14718  0.25187310
4.  MA{2}                        -0.137833740  0.137726044     -1.00078  0.31743127
5.  MA{3}                         0.082433978  0.107368024      0.76777  0.44299730

Inverse Roots of AR and MA polynomials
Absolute Value of MA Roots
1   0.379356
2   0.425718
3   0.510432

Absolute Value of AR Roots
1   0.290355
2   1.000000

```


<p align="center">
  <img src = "https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi311.png" width="45%">
  <img src = "https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi312.png" width="45%">
</p>

### Forecasts:
```
**Random Simulation Forecast:**  
forecast for 2025:05    2283.81536  
forecast for 2025:11    2240.53694  
forecast for 2029:01    2614.70652 
```
<p align="center">
  <img src="https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi313.png" width="70%">
</p>
```
**Bootstrap Forecast:**  
forecast for 2025:05    2376.59793  
forecast for 2025:11    2529.02747  
forecast for 2029:01    2736.78437
```
<p align="center">
  <img src="https://github.com/chuckles023/Post-Pandemic-Durable-Consumer-Spending-Analysis/blob/main/images/pi314.png" width="70%">
</p>
## Conclusion:

From the research I can determine that excess household savings are in fact going down, but I believe that they will deviate towards the trend and will recover over the next couple years as we see inflation cool down, as it was at its peak in June 2022\.  Consumer spending overall was very different during the pandemic which had an effect on how savings were used, which will also return to the pre-pandemic trend. The stochastic trend model predicts a sustained increase in durable goods spending through 2029, providing a robust basis for investment decisions. While uncertainties remain, such as potential economic shocks, the forecast supports confidence in market stability and growth in the durable goods sector.  

**Sources:**

1. [**https://www.frbsf.org/research-and-insights/publications/economic-letter/2023/05/rise-and-fall-of-pandemic-excess-savings/**](https://www.frbsf.org/research-and-insights/publications/economic-letter/2023/05/rise-and-fall-of-pandemic-excess-savings/)

2. [**https://www.frbsf.org/research-and-insights/data-and-indicators/pandemic-era-excess-savings/**](https://www.frbsf.org/research-and-insights/data-and-indicators/pandemic-era-excess-savings/)

3. [**https://www.federalreserve.gov/econres/notes/feds-notes/the-unusual-composition-of-demand-during-the-pandemic-20210114.html**](https://www.federalreserve.gov/econres/notes/feds-notes/the-unusual-composition-of-demand-during-the-pandemic-20210114.html) 

4. [**https://www.wsj.com/articles/consumers-are-pivoting-spending-to-services-like-dining-and-travel-11643797808**](https://www.wsj.com/articles/consumers-are-pivoting-spending-to-services-like-dining-and-travel-11643797808) 

**Google Doc Backup: [https://docs.google.com/document/d/1Y-tgRmOcSbbQkaNLWTNiM6cHRU4rmoXSLNVfwsDYYpE/edit?usp=sharing](https://docs.google.com/document/d/1Y-tgRmOcSbbQkaNLWTNiM6cHRU4rmoXSLNVfwsDYYpE/edit?usp=sharing)** 
