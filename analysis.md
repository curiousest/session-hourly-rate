## Initial exploration

[Data exploration notebook](hourly_explore.ipynb)

I started by exploring the data with basic counts/averages/max/mins and extracting some time features that seemed relevant. Then I explored visualizing hourly rate vs. fill rate to understand the high-level relationship. I found that there was different amounts of data for different hourly rates, so I made visual adjustments to the graphs.

## Data visualization

[Data visualization notebook](hourly_visualization.ipynb)

First, I made high level summary visualizations. Fill rates seem to trend upwards to 90, then plateau. There are some off-trendline fill rates at some hourly rates.

### Overall fill rate (%)

![Hourly Rate Percent Filled](hourly_rate_filled_unfilled_pct.png)

### Overall absolute filled/unfilled numbers

![Absolute Hourly Rate](hourly_rate_filled_unfilled_absolute.png)

Next, I made similar visualizations that take into consideration several time features. Some differences were notable:

* Morning > Afternoon > Night
* Lower fill rate of long sessions
* Weekend fill rates are worse

### For sessions that occurred at a particular time of day

#### Morning

![](hourly_rate_morning.png)

#### Afternoon

![](hourly_rate_afternoon.png)

#### Evening

![](hourly_rate_evening.png)

### For sessions that were a particular length

#### Short

![](hourly_rate_short.png)

#### Medium

![](hourly_rate_medium.png)

#### Long

![](hourly_rate_long.png)

### For sessions that were a particular length

#### Short

![](hourly_rate_short.png)

#### Medium

![](hourly_rate_medium.png)

#### Long

![](hourly_rate_long.png)

### For sessions starting on each day of the week

#### Monday 

![](hourly_rate_monday.png)

#### Tuesday

![](hourly_rate_tuesday.png)

#### Wednesday

![](hourly_rate_wednesday.png)

#### Thursday

![](hourly_rate_thursday.png)

#### Friday

![](hourly_rate_friday.png)

#### Saturday

![](hourly_rate_saturday.png)

#### Sunday

![](hourly_rate_sunday.png)

## Predictive Analysis

[Predictive analysis notebook](hourly_predictive_analysis.ipynb)

Next, I made a predictive model to see if the features could be used to predict fill rate, and whether hourly rate was a useful feature in predicting fill rate (meaning it influences fill rate and isn't explained by other features).

First, I made a decision tree model. I found that it was overfitting against the time features because it performed more poorly using time features than not using them. I guessed that this was because there wasn't enough data for some hourly rates, so I used a Support Vector Regressor.

The difference in predictive power between using or not using hourly rate as a feature was 0.35% on the F1 score and 0.5% accuracy (when also using practice id, ccg id, and time features). This means hourly rate is mostly explained by those other features.

This could, for example, mean:

* If the session is at a different time of day, it could have a propensity to have a different hourly rate
* Sessions in different ccgs correlate with certain hourly rates
* Sessions at different practices correlate with certain hourly rates
