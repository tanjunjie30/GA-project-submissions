# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Exploring climate data of Singapore

### Overview

Situated near the Equator, the island has year-round temperatures that hover around 88 degrees Fahrenheit. Like the rest of the tropics, it has the extra burden of high humidity, at an average 84 percent.

Consequently, people who enjoy outdoor activities are often contending against the weather. This project aims to identify climactic patterns  in Singapore so that Singaporeans are able to understand how best to plan their outdoor activities. 


### Problem Statement

One of the biggest headache with outdoor tennis is that we are mostly at mercy of the weather. We book the court, it rains, and we either have to forgo the booking or go through the troublesome process of seeking a refund. 

The objective of this research is to give tennis players a better idea of climactic patterns in Singapore so that they may use it to better plan their tennis court bookings.

---

### Datasets

#### Provided Data

There are 3 datasets included in the [`data`](./data/) folder for this project. These correponds to rainfall and humidity information.

* merged_humidity.csv
* merged_rainfall.csv
* wbt_with_air.csv


#### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|total_rainfall|float|merged_rainfall|Total rainfall in mm| 
|maximum_rainfall_in_a_day|float|merged_rainfall|Max rainfall in a day in mm|
|no_of_rainy_days|int|merged_rainfall|Number of rainy days|
|year|int|merged_rainfall|Year for which data was taken| 
|mth|int|merged_rainfall|Month for which data was taken| 
|average_rainfall_per_day|float|merged_rainfall|Total Rainfall/Number of rainy days in the month, in mm|
|monthly_probability_of_rain|float|merged_rainfall|Number of rainy days in the month/Number of calendar days in the month|
|mean_rh|float|merged_humidity|mean relative humidity for the month|
|mean_sunshine_hrs|float|merged_humidity|mean sunshine hours per day for the month|
|mean_temp|float|merged_humidity|mean surface air temperature for the month|
|year|int|merged_humidity|Year for which data was taken| 
|mth|int|merged_humidity|Month for which data was taken|
|wbt_time|int|wbt_with_air|Hour for which reading for the wet bulb temperature was taken|
|wet_bulb_temperature|float|wbt_with_air|Wet bulb temperature reading|
|year|int|wbt_with_air|Year for which data was taken| 
|mth|int|wbt_with_air|Month for which data was taken|
|mean_temp|float|wbt_with_air|mean surface air temperature for the month|
|bulb_minus_air_temp|float|wbt_with_air|Hourly difference between wet bulb and monthly mean surface air temperature|


All sources of data above can be downloaded from (https://data.gov.sg/dataset). Included below are original dataset links that have been used to prepare my 3 datasets for analysis.


* [`rainfall-monthly-number-of-rain-days.csv`](./data/rainfall-monthly-number-of-rain-days.csv): Monthly number of rain days from 1982 to 2022. A day is considered to have “rained” if the total rainfall for that day is 0.2mm or more.
* [`rainfall-monthly-total.csv`](./data/rainfall-monthly-total.csv): Monthly total rain recorded in mm(millimeters) from 1982 to 2022
* [Relative Humidity](https://data.gov.sg/dataset/relative-humidity-monthly-mean)
* [Monthly Maximum Daily Rainfall](https://data.gov.sg/dataset/rainfall-monthly-maximum-daily-total)
* [Hourly wet bulb temperature](https://data.gov.sg/dataset/wet-bulb-temperature-hourly)
* [Monthly mean sunshine hours](https://data.gov.sg/dataset/sunshine-duration-monthly-mean-daily-duration)
* [Surface Air Temperature](https://data.gov.sg/dataset/surface-air-temperature-mean-daily-minimum)

---

### Conclusions and Recommendations


* Try to avoid the Northeast Monsoon months (Nov/Dec/Jan) if you are playing tennis.
* If you want to take your best chance at the weather, book the 12pm-1pm slot.
* On average, the least likely hours to rain are during 10am-1pm.
* Global warming is real! 
* Rising air temperatures and falling humidity in recent years are a potent combination that increases your risk of heat injuries due to increased rate of dehydration.
* **BE SURE TO DRINK MORE WATER!**

---

### Technical Report Starter Code

Future projects will require you to decide on the entire structure of your technical report. Here, we provide you with [starter code](./code/starter-code.ipynb) in a Jupyter notebook that will help to guide your data exploration and analysis. **If you choose to edit the core structure of this notebook, make sure you don't exclude any of the requested operations**.

---

### Suggested Resources

Here's a link on [how to give a good lightning talk](https://www.semrush.com/blog/16-ways-to-prepare-for-a-lightning-talk/), which provides some good recommendations for short presentations.

[Here's a great summary](https://towardsdatascience.com/storytelling-with-data-a-data-visualization-guide-for-business-professionals-97d50512b407) of the main points of the book _Storytelling with Data_, which I can't recommend enough. [Here's a blog post](http://www.storytellingwithdata.com/blog/2017/8/9/my-guiding-principles) by the author about his guiding principles for visualizations.

---


