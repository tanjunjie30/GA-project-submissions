# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 


# Project 1: Exploring climate data of Singapore

### Overview

Situated near the Equator, the island has year-round temperatures that hover around 88 degrees Fahrenheit. Like the rest of the tropics, it has the extra burden of high humidity, at an average 84 percent.

Consequently, people who enjoy outdoor activities are often at the mercy of the weather.  

This project aims to identify climactic patterns  in Singapore so that Singaporeans are able to understand how best to plan their outdoor activities.  


### Problem Statement

One of the biggest headache with outdoor tennis is that we are mostly at mercy of the weather. We book the court, it rains, and we either have to forgo the booking or go through the troublesome process of seeking a refund. 

The objective of this research is to give tennis players a better idea of climactic patterns in Singapore so that they may use it to better plan their tennis court bookings.

---

### Datasets

#### Provided Data

There are two groups of datasets included in the [`data`](./data/) folder for this project. These correpond to rainfall and humidity information.  

1. Original datasets (*source:*  https://data.gov.sg/dataset)  
  
  * [`rainfall-monthly-number-of-rain-days.csv`](./data/rainfall-monthly-number-of-rain-days.csv): Monthly number of rain days from 1982 to 2022. A day is considered to have “rained” if the total rainfall for that day is 0.2mm or more.
  * [`rainfall-monthly-total.csv`](./data/rainfall-monthly-total.csv): Monthly total rain recorded in mm(millimeters) from 1982 to 2022
  * [Relative Humidity](https://data.gov.sg/dataset/relative-humidity-monthly-mean)
  * [Monthly Maximum Daily Rainfall](https://data.gov.sg/dataset/rainfall-monthly-maximum-daily-total)
  * [Hourly wet bulb temperature](https://data.gov.sg/dataset/wet-bulb-temperature-hourly)
  * [Monthly mean sunshine hours](https://data.gov.sg/dataset/sunshine-duration-monthly-mean-daily-duration)
  * [Surface Air Temperature](https://data.gov.sg/dataset/surface-air-temperature-mean-daily-minimum)  
  

2. Processed datasets - cleaned, grouped and merged from the Original datasets for use in this analysis

  * merged_humidity.csv
  * merged_rainfall.csv
  * wbt_with_air.csv


#### Data Dictionary

|Feature|Data Type|Unit|Dataset|Description|Data Source|
|:---|---|:---:|---|---:|---|
|total_rainfall|float|mm|merged_rainfall|Total rainfall|rainfall-monthly-total
|maximum_rainfall_in_a_day|float|mm|merged_rainfall|Maximum rainfall in a day|rainfall-monthly-highest-daily-total
|no_of_rainy_days|int|days|merged_rainfall|Number of rainy days|rainfall-monthly-number-of-rain-days
|year|int|Numeric(General)|merged_rainfall|Year for which data was taken, from 1982 to 2022|
|mth|int|Numeric(General)|merged_rainfall|Month for which data was taken, from 1 to 12| 
|average_rainfall_per_day|float|mm|merged_rainfall|Total Rainfall/Number of rainy days in the month|
|monthly_probability_of_rain|float|Decimal(Percentage)|merged_rainfall|Number of rainy days in the month/Number of calendar days in the month|
|mean_rh|float|Numeric(Percentage)|merged_humidity|Monthly mean relative humidity|relative-humidity-monthly-mean
|mean_sunshine_hrs|float|Hour|merged_humidity|Monthly Mean Daily Sunshine Duration|sunshine-duration-monthly-mean-daily-duration
|mean_temp|float|Degree Celsius|merged_humidity|Monthly Mean Daily Minimum Temperature|surface-air-temperature-monthly-mean
|year|int|Numeric(General)|merged_humidity|Year for which data was taken, from 1982-2022| 
|mth|int|Numeric(General)|merged_humidity|Month for which data was taken, from 1 to 12|
|wbt_time|int|Hour|wbt_with_air|the hour is from 1 to 24|wet-bulb-temperature-hourly
|wet_bulb_temperature|float|Degree Celsius|wbt_with_air|Wet Bulb Temperature-Hourly|wet-bulb-temperature-hourly
|year|int|Numeric(General)|wbt_with_air|Year for which data was taken, from 1982-2022| 
|mth|int|Numeric(General)|wbt_with_air|Month for which data was taken, from 1 to 12|
|mean_temp|float|Degree Celsius|wbt_with_air|Monthly Mean Daily Minimum Temperature|surface-air-temperature-monthly-mean
|bulb_minus_air_temp|float|Degree Celsius|wbt_with_air|Hourly difference between wet bulb and monthly mean surface air temperature|

---  
     
### Exploratory Analysis


* In the last seven years, Singapore has been seeing major shifts in their climate as a result of global warming. Most notably, the average surface air temperatures have been gradually rising over the last decade from 27.5 degree Celsius to 28.5 degree celsius, leading to structural changes in humidity conditions as well.    


* In instances when the mean air temperatures spiked, as in 1998-2000 and 2015-present, the mean relative humidity dropped sharply in tandem. While this suggests an inverse relationship between the two factors, it is inconclusive of its causality due to a reflexive relationship between the two, in addition to a complex array of other climactic factors not studied here.   


* Despite rising temperatures and falling humidity, Singaporeans are not seeing a corresponding increase in mean sunshine hours as measurements suggest continued regression to the historical mean of 5.8 sunshine hours per day. If anything, Singapore recorded slightly more sunshine hours by an average of 0.5hour since 2015 due likely to the lower air humidity that has resulted in less cloud cover and thus less rainfall.    


* A strong positive correlation exists between the mean air humidity and probability of rainfall per month. With the exception of Year 2021 which has recorded its wettest year since 1980 as a result of the La Nina Phenomenon, the total rainfall in the last seven years has in fact declined substantially due to the sharp drops in humidity. Even the wettest Northeast Monsoon has recorded much less rainfall for the same period as have the annual number of rainy days.    


* Among the months of the Northeast Monsoon, November and December are the wettest with nearly 60% of the month raining heavily on average. While January has a lower probability of rain at around 43%, rainfall during this month is the most unpredictable in terms of variability and magnitude. Tennis players should try to avoid playing outdoor tennis during these three months of monsoon surge.    


* For any outdoor tennis player concerned with rainfall, they should be glad that less humidity correlates well with less rainfall and a lower probability of rain. Therefore, playing during the least humid hours of the day should provide the greatest odds of avoiding the rain. From the differences between the wet bulb temperatures and its corresponding monthly mean air temperatures, this study found that humidity tends to fall during the 10am-1pm window on an average daily basis. 12pm is the optimal time for the best odds of avoiding rain as the sun is at its hottest. Nonetheless , there is a wide range in humidity conditions during this window too so a large degree of uncertainty exists. 


---

### Conclusions and Recommendations


* Try to avoid the Northeast Monsoon months (Nov/Dec/Jan) if you are playing tennis.
* On average, the least likely hours to rain are during 10am-1pm.
* If you want to take your best chance at the weather, book the 12pm-1pm slot.
* Global warming is real! 
* Rising air temperatures and falling humidity in recent years are a potent combination that increases your risk of heat injuries due to increased rate of dehydration.
* **IF YOU ARE PLAYING, BE SURE TO DRINK MORE WATER!**

---

