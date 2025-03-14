# Predicting Power Outage Causes Across U.S. States

## Introduction 
|Column                            | Description |
|---|---                           |
|`'MONTH'`                         | Month during which the outage took place |
|`'U.S._STATE'`                    | State the outage occurred in |
|`'OUTAGE.DURATION'`               | Duration of outage events (in minutes) |
|`'CUSTOMERS.AFFECTED'`            | Number of customers affected by the power outage event |
|`'CAUSE.CATEGORY'`                | Categories of all the events causing the major power outages |
|`'ANOMALY.LEVEL'`                 | The oceanic El Niño/La Niña (ONI) index referring to the cold and warm episodes by season |
|`'RES.CUSTOMERS'`                 | Annual number of customers served in the residential electricity sector of the U.S. state |


## Data Cleaning and EDA


### Data Cleaning 
  
### Univariate Analysis

<iframe
  src="plots/Univariate_Outages_Years.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="plots/us_power_outages_map.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="plots/combined_power_outages_state.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Bivariate Analysis

<iframe
  src="plots/Sunburst_State_Cause.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="plots/Bivariate_Duration_State.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Interesting Aggregates

<iframe
  src="plots/df_agg.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Assessment of Missingness

### NMAR Analysis

After analyzing different columns, we thought `'CUSTOMERS.AFFECTED'`'s missingness to be NMAR. Since the power outage durations can be as extreme as 108k minutes, some companies might tend to not record or report such long durations of outages to avoid negative publicity. It might also be the case that data where only a few customers would have been affected might not be reported due to the numbers being small and insignificant. About a third of the rows of the top 50 highest reported outage durations had their corresponding `'CUSTOMERS.AFFECTED'` value empty, and about half of them either were not reported or had suspiciously low values of under 10 customers affected. This led us to believe that `'CUSTOMERS.AFFECTED'` could be NMAR on `'OUTAGE.DURATION'`.

#### What data could we collect to explain the missingness? 

The main features that could help us identify the true cause of missingness would be gettint to know the Utility company policies and thresholds with regards to collecting and reporting the data. Other data features like data reporting history and analysis of trends, potential state-to-state varying regulatory requirements, company structure, media coverage, etc. 

### Missingness Dependency


   
## Hypothesis Testing

### Introducing our Hypothesis

In this analysis, we set out to investigate whether certain factors, such as states, cause categories, and months, influence the duration of power outages in the United States. Specifically, we aimed to test whether the distribution of outage durations is proportionally related to the frequency of outages in different states, cause categories, and months. We hypothesized that certain factors could cause systematic differences in outage durations, suggesting that some regions, causes, or times of the year might experience longer outages than others due to inherent infrastructural or environmental challenges.

When conducting this hypothesis testing, we are making a key assumption: If the system is fair and there is no underlying cause driving differences in outage duration, then states with more outages should, on average, experience longer outage durations. This assumption is based on the idea that, generally speaking, states with more frequent outages might face more systemic challenges (e.g. infrastructure limitations), which could result in longer durations.

Thus, under the null hypothesis, we assume that the distribution of outage durations should be proportional to the distribution of outage frequencies across states.


### Hypothesis Testing (Across States)

**Null Hypothesis** : The distribution of power outage durations across states is proportional to the distribution of the number of outages per state.

Any observed difference (TVD) is due to random variation rather than a true underlying effect.

**Alternative Hypothesis** : The distribution of power outage durations is not proportional to the number of outages per state.

**Test Statistic** : TVD 

#### Test Visualization

<iframe
  src="plots/TVD_Dist_Out_States.html"
  width="800"
  height="400"
  frameborder="0"
></iframe>

Our observed TVD lied in the extreme right tail of Null distribution (obtained from permutation tests) which provides strong evidence that outage durations are not randomly assigned across states.

Hence we **reject the Null Hypothesis**. There are likely systematic factors (e.g., infrastructure & weather) that cause certain states to have disproportionately longer outages than their outage frequency would suggest.


### Hypothesis Testing (Across Cause Categories)

**Null Hypothesis**: The distribution of power outage durations across different cause categories is proportional to the distribution of the number of outages in each cause category. Any observed difference (TVD) is due to random variation rather than a true underlying effect.

**Alternative Hypothesis**: The distribution of power outage durations is not proportional to the number of outages in each cause category.

**Test Statistic**: TVD

#### Test Visualization

<iframe
  src="plots/HTCausePlot2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Our observed TVD lied in the extreme right tail of the null distribution (obtained from permutation tests), which provides strong evidence that outage durations are not randomly assigned across cause categories.

Hence, we **reject the Null hypothesis**. There are likely systematic factors (e.g., infrastructure, severity of weather events, and other causes) that lead to disproportionately longer outages in certain cause categories compared to their outage frequency.

### Hypothesis Testing (Across Month)

**Null Hypothesis**: The distribution of power outage durations across different months is proportional to the distribution of the number of outages in each month. Any observed difference (TVD) is due to random variation rather than a true underlying effect.

**Alternative Hypothesis**: The distribution of power outage durations is not proportional to the number of outages in each month.

**Test Statistic**: TVD

<iframe
  src="plots/HTMonthPlot3.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Our observed TVD did not lie in the extreme right tail of the null distribution (obtained from permutation tests), and the p-value was not sufficiently small. This suggests that the observed difference in outage durations across months is likely due to random variation.

We fail to reject the null hypothesis. The analysis indicates that the outage duration and frequency seem to have a relationship across months, and there is no strong evidence to suggest that certain months cause disproportionately longer outages than would be expected based on the number of outages.

### Conclusion

**Across States**: We found strong evidence against the null hypothesis, indicating that certain states have disproportionately longer outage durations than would be expected based on their outage frequency. This suggests that inherent differences between states, such as infrastructure likely contribute to longer durations.

**Across Cause Categories**: We observed that certain causes of outages (e.g., severe weather events) are associated with longer durations, supporting the hypothesis that specific causes lead to more prolonged outages.

**Across Months**: Interestingly, we failed to reject the null hypothesis for months, as the p-value was not sufficiently small, indicating that the variation in outage durations across months is likely due to random variation. This suggests that, unlike states and causes, month-to-month differences in outage duration do not exhibit a strong systematic pattern.


## Framing a Prediction Problem 
### Problem Identification

## Baseline Model

## Final Model

## Fairness Analysis
