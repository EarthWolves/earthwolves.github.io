# Predicting Power Outage Causes Across U.S. States

## Introduction 
 |Column                |Description|
|---|---        |
|`'MONTH'`|Month during which the outage took place|
|`'U.S._STATE'`|State the outage occurred in|
|`'OUTAGE.DURATION'`|Duration of outage events (in minutes)|
|`'CUSTOMERS.AFFECTED'`|Number of customers affected by the power outage event|
|`'CAUSE.CATEGORY'`|Categories of all the events causing the major power outages|
|`'ANOMALY.LEVEL'`|Oceanic El Niño/La Niña (ONI) index referring to the cold and warm episodes by season|
|`'RESIDENTIAL.CUSTOMERS'`| |


## Data Cleaning and EDA


### Data Cleaning 
  
### Univariate Analysis

<iframe
  src="Univariate_Outages_Years.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="us_power_outages_map.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Bivariate Analysis

<iframe
  src="Sunburst_State_Cause.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="Bivariate_Duration_State.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Interesting Aggregates

## Assessment of Missingness

### NMAR Analysis

### Missingness Dependency
   
## Hypothesis Testing

<iframe
  src="TVD_Dist_Out_States.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="HTCausePlot2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="HTMonthPlot3.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Framing a Prediction Problem 
### Problem Identification

## Baseline Model

## Final Model

## Fairness Analysis
