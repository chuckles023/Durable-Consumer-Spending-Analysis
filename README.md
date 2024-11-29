# Post Pandemic Durable Consumer Spending Analysis
March 21 2024

Durable goods play an important role in forecasting demand and understanding consumer behavior.  Durable goods are physical products with longer life spans and are associated with significant investment and infrequent purchase cycles.  They are very sensitive to economic conditions, making them a good indicator of consumer confidence.  As the economy recovers from the Covid-19 downturn, understanding how durable goods will perform over the next 5 years can be important to inventory decision making, helping businesses align supply with shifting customer demand.  

An important aspect of the pandemic and ensuing economic downturn was the effect of the stimulus checks on savings held by consumers.  Higher consumer savings often lead to increased demand for durable goods, as individuals feel more financially secure and are willing to make significant purchases.  Understanding when these savings will be depleted and how this will influence consumption will help contextualize our forecasts.  

In January 2021, the FED released a report discussing demand during the pandemic.  They found that during most recessions, household spending on goods and housing tends to fall and services spending tends to respond weakly to the business cycle.  Surprisingly, the opposite was true during the pandemic, where services spending remained weak for multiple quarters while goods spending and housing investment were able to rebound and rise above pre-pandemic levels rather quickly.  One main reason for this observation was the role of social distancing in how consumers were behaving during the recession.  

According to the FED, two metrics for housing activity, new construction and home sales, saw an initial drop at the start of the pandemic but recovered quickly and rose above pre-pandemic levels.  A combination of different factors led to the resilience in the market.  Record low mortgage rates and the availability of online or limited contact tools for home buying encouraged activity.  New homebuyers were also more likely to have relatively high income, a sect of employees which experienced less unemployment comparatively.  These higher income households make up most of the effect in the rebound of housing activity as existing home sale growth is far greater in sales of $500,000+ compared to lower prices.  Ultimately, the characteristics of the pandemic changed people’s relationships with their home, maintaining and strengthening the market.  

Despite restrictions on leaving home, spending from CARES Act stimulus checks resembled pre-pandemic patterns, with a notable increase in goods spending following the payout of stimulus checks, especially online. While spending on durable goods initially fell below pre-COVID levels, it eventually surpassed expectations by the end of 2020\.  The effects of the shutdown caused consumers to shift from using their disposable income to purchase services towards a focus on the purchase of goods.  The pandemic made it much harder to eat out and travel.  Now in a post pandemic era, we are seeing a reversion of this trend.  Two years before the pandemic, personal consumption of durable and nondurable goods was at 31%, increasing to 36% in March and April of 2021\.  After the vaccine was released, we saw a decrease back down to 34% in December 2021\.  Consumer spending became strained due to supply chain constraints, rising prices from inflation, and diminishing government stimulus funds.  Travel and dining also saw an increase as people became more comfortable going out and social distancing measures were withdrawn.  

A study in early 2023 by Abdelrahman and Oliveira examined Pandemic Era excess savings which are defined as the difference between actual savings and the pre-pandemic trend.  What they found was that a combination of fiscal support from the government and a drop in household spending caused household savings to see a rise in the overall US economy, well above the pre-pandemic trend line.  When economic activity began to recover after the lockdown, households used these savings to support their new spending.  By the end of 2021 these savings had started to dry up, dipping below the pre pandemic trend.  

Abdelrahman and Oliveira determined that by March 2023, only $500 billion of the $2.1 Trillion in pandemic savings in the economy remained. Data revisions released by the Bureau of Economic Analysis after their initial study showed that household spending increased and household disposable income decreased in the last quarter of 2022 and the 1st quarter of 2023\.  They also found that consumer spending continued to grow going into the 2nd quarter.  Their new estimates would have aggregate excess savings all the way down to $190 billion by June and all the way gone by the 3rd quarter of 2023\.  Since its peak in August 2021, personal savings has been below pre-pandemic trend.  Compared to other recessions, aggregate excess savings performed in a completely different manner, peaking around 12 to 18 months and tapering off by 36\.  In other recessions like 2008, 2001, or 1980, aggregate excess savings slowly recovered over the course of a few years in a steady and predictable fashion.  

# Method:

To predict the growth of consumer spending over the next 12 months, we will use the metric PCEDG which measures personal consumption expenditures on durable goods.  We will create 2 competing models, one with a deterministic trend and one with a stochastic trend and forecast PCEDG. They will be trained on the PCEDG time series dating up to the 2008 financial crisis.  Then we will use the Granger Newbold test to determine which model is more accurate and use that model to forecast PCEDG over the next 12 months.  

# Econometric Analysis:

**![][image1]**  
**A graph of PCEDG (1984 \- Present)**  
**Unit: Billions of Dollars**  
**Frequency: Monthly**

| Dickey-Fuller Unit Root Test, Series LPCE Regression Run From 1984:05 to 2009:01 Observations        298 With intercept and trend With 3 lags chosen from 4 by AIC Null is unit root. Reject in left tail. Sig Level    Crit Value 1%(\*\*)         \-3.99236 5%(\*)          \-3.42635 10%            \-3.13610 T-Statistic     0.52263  | Dickey-Fuller Unit Root Test, Series DIFFPCE Regression Run From 1984:04 to 2009:01 Observations        299 With intercept and trend With 2 lags chosen from 4 by AIC Null is unit root. Reject in left tail. Sig Level    Crit Value 1%(\*\*)        \-3.9923 5%(\*)         \-3.4263 10%           \-3.1361 T-Statistic  \-14.4328\*\*  |
| :---- | :---- |

**First we run a Dickey-Fuller Unit Root Test on 2 variables to determine if there is a unit root in the data.  LPCE takes the log of PCEDG to stabilize variance in the data.  DIFFPCE is the first difference of LPCE which further removes trends from the data.  The T statistic from the test on the left is 0.52263, greater than the critical value, so we fail to reject the null hypothesis of a unit root in the LPCE series.  We now know that the data has a stochastic trend.  The T statistic of the test on the right is \-14.4328, less than the critical value, so we reject the null hypothesis of a unit root.  We have removed the trend from the data.**      

## Modeling Personal Consumption Expenditures(durable goods) using a Deterministic Trend

Linear Regression \- Estimation by Least Squares  
Dependent Variable LPCE  
Monthly Data From 1984:01 To 2009:01  
Usable Observations                       301  
Degrees of Freedom                        299  
Centered R^2                        0.9725424  
R-Bar^2                             0.9724506  
Uncentered R^2                      0.9999046  
Mean of Dependent Variable       6.5286337876  
Std Error of Dependent Variable  0.3860471760  
Standard Error of Estimate       0.0640761627  
Sum of Squared Residuals         1.2276206330  
Regression F(1,299)                10590.5272  
Significance Level of F             0.0000000  
Log Likelihood                       400.9554  
Durbin-Watson Statistic                0.1893

    Variable                        Coeff      Std Error      T-Stat      Signif  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
1\.  Constant                     1.4589368592 0.0494015165     29.53223  0.00000000  
2\.  TREND                        0.0043741992 0.0000425050    102.91029  0.00000000

**This is the initial linear regression results of the Log of PCEDG.  Taking the Log of the original time series allows us to remove some of the trend from the data.**    
**![][image2]![][image3]**  
**This data is the result of fitting the model using the Box Jenkins ARMA model.  Using bjautofit to find the parameters AR=3 and MA=3.**  

Forecast Analysis for PCEFOR  
From 2009:02 to 2014:12  
Mean Error                 \-0.0887747  
Mean Absolute Error         0.0936523  
Root Mean Square Error      0.1139442  
Mean Square Error            0.012983  
Theil's U                  153.145408

Mean Pct Error              \-0.012800  
Mean Abs Pct Error           0.013504  
Root Mean Square Pct Error   0.016431  
Theil's Relative U         153.980148

Theil Inequality Measure     0.008164  
  Bias                       0.607007  
  Variance                   0.372274  
  Covariance                 0.020719

## Modeling Personal Consumption Expenditures(durable goods) Using an Stochastic Trend:

Box-Jenkins \- Estimation by LS Gauss-Newton  
Convergence in    42 Iterations. Final criterion was  0.0000071 \<=  0.0000100

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
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
1\.  CONSTANT                      0.003639446  0.000864197      4.21136  0.00003372  
2\.  AR{1}                         0.464862437  0.233597543      1.99001  0.04750909  
3\.  MA{1}                        \-0.897620343  0.235492944     \-3.81167  0.00016793  
4\.  MA{2}                         0.062120168  0.130665772      0.47541  0.63484348  
5\.  MA{3}                         0.147139486  0.060113638      2.44769  0.01495840

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

## Comparing the 2 models using the Granger-Newbold Test:

Granger-Newbold Forecast Comparison Test  
Forecasts of LPCE over 2009:02 to 2014:12

Forecast Test Stat P(GN\>x)  
PCEFOR     20.1132 0.00000  
PCEFOR2   \-20.1132 1.00000

**Deterministic Trend:					ARIMA Model:**  
**![][image4]![][image5]**

| Correlations of PCEFOR Errors Monthly Data From 2009:02 To 2014:12 Lag     ACF        PACF    1   0.970391   0.970391    2   0.954876   0.226546    3   0.947539   0.199033    4   0.934967  \-0.005741    5   0.920045  \-0.046836    6   0.904972  \-0.054346    7   0.896462   0.088038    8   0.872603  \-0.236849 Ljung-Box Q-Statistics Lags  Statistic Signif Lvl    1     69.723   0.000000    2    138.213   0.000000    3    206.646   0.000000    4    274.270   0.000000    5    340.744   0.000000    6    406.048   0.000000    7    471.131   0.000000    8    533.774   0.000000  | Correlations of PCEFOR2 Errors Monthly Data From 2009:02 To 2014:12 Lag     ACF        PACF    1    0.32363    0.32363    2    0.05188   \-0.05904    3    0.03070    0.03589    4   \-0.07522   \-0.10519    5   \-0.19145   \-0.15039    6   \-0.23875   \-0.15164    7   \-0.08414    0.04367    8   \-0.19210   \-0.20994 Ljung-Box Q-Statistics Lags  Statistic Signif Lvl    1      7.755   0.005357    2      7.957   0.018713    3      8.029   0.045419    4      8.467   0.075908    5     11.345   0.044953    6     15.890   0.014355    7     16.464   0.021201    8     19.500   0.012403  |
| :---- | :---- |

When comparing the 2 models, we find that the stochastic trend proves to be a better model at predicting consumer expenditure through the test statistic for the Granger-Newbold test and when comparing the errors, the stochastic trend also has a higher q statistic.  

## Forecasting 2024-2029 using the ARIMA MODEL:

Box-Jenkins \- Estimation by LS Gauss-Newton  
Convergence in    18 Iterations. Final criterion was  0.0000059 \<=  0.0000100

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
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
1\.  CONSTANT                      0.003844793  0.000683903      5.62184  0.00000003  
2\.  AR{1}                         0.290354553  0.484454476      0.59934  0.54922383  
3\.  MA{1}                        \-0.556794226  0.485359352     \-1.14718  0.25187310  
4\.  MA{2}                        \-0.137833740  0.137726044     \-1.00078  0.31743127  
5\.  MA{3}                         0.082433978  0.107368024      0.76777  0.44299730

**Conclusion:**

From the research I can determine that excess household savings are in fact going down, but I believe that they will deviate towards the trend and will recover over the next couple years as we see inflation cool down, as it was at its peak in June 2022\.  Consumer spending overall was very different during the pandemic which had an effect on how savings were used, which will also return to the pre-pandemic trend. With this information and our forecast showing a continued increase in consumer goods spending on durable goods, I think that we can make an investment decision to bet on a continued increase in consumer goods spending and we can assume that the market will not crash, barring a large unforeseen negative shock.  

**Sources:**

1. [**https://www.frbsf.org/research-and-insights/publications/economic-letter/2023/05/rise-and-fall-of-pandemic-excess-savings/**](https://www.frbsf.org/research-and-insights/publications/economic-letter/2023/05/rise-and-fall-of-pandemic-excess-savings/)

2. [**https://www.frbsf.org/research-and-insights/data-and-indicators/pandemic-era-excess-savings/**](https://www.frbsf.org/research-and-insights/data-and-indicators/pandemic-era-excess-savings/)

3. [**https://www.federalreserve.gov/econres/notes/feds-notes/the-unusual-composition-of-demand-during-the-pandemic-20210114.html**](https://www.federalreserve.gov/econres/notes/feds-notes/the-unusual-composition-of-demand-during-the-pandemic-20210114.html)

4. [**https://www.wsj.com/articles/consumers-are-pivoting-spending-to-services-like-dining-and-travel-11643797808**](https://www.wsj.com/articles/consumers-are-pivoting-spending-to-services-like-dining-and-travel-11643797808)
