# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) 


# Project 4: West Nile Virus Prediction


### Problem Statement

West Nile virus is most commonly spread to humans through infected mosquitos. Around 20% of people who become infected with the virus develop symptoms ranging from a persistent fever, to serious neurological illnesses that can result in death. The City of Chicago and CPHD needs a model that can help them to predict more efficiently and effectively where and when the mosquitos will become virulent so that they can allocate resources towards preventing transmission of this potentially deadly virus. 

---

### Datasets

#### Provided Data

The main datasets used will be from Kaggle.

1. **Original datasets** (*source:*  https://www.kaggle.com/competitions/predict-west-nile-virus/data)
                
  
---  
     
### Exploratory Analysis

***1) EDA on Train and Test sets***  

In this section, two new features, `NumMosquitos_cluster` and `trap_cluster` have been engineered to encode information on `NumMosquitos` and `WnvPresent` respectively into the 151 unique `Trap` by means of a clustering algorithm. Each new feature has three unique values of 1,2,3 where 1 has the smallest cluster of NumMosquitos or WnvPresent and 3 being the biggest cluster. The reasoning is that `Trap` close to each other in proximity is likely to have similar levels of risk.   

This clustering allows us to encode information otherwise absent in the `test` dataset. Both features also provide information on the level of a virulent risk.  
  
***2) EDA on Weather set***  

Important findings from this exploratory work on the `weather` dataset includes:  
* Temperatures tend to peak around Jul-Aug while the incidences of WNV tend to peak in Aug when the US is in the height of its summer. From a weekly trend analysis, we can see here that the spike in WnvPresent total count tends to happen in week 33-34 (mid-August).  
* Optimal temp for mosquitos to thrive appears to be between 70-80 degreeF. If the previous month's temp is coming within this optimal range, we can expect the current month cases of WnvPresent to start peaking.  
* DewPoint is highly correlated with Temperatures so we will have to re-engineer this feature to derive the humidity feature if this is to be used.  
* Daily mean total NumMosquitos is quite positively correlated with WnvPresent of +0.33
* Among the Temperature features, Tmin has higher positive correlation with NumMosquitos of +0.36; Tavg has +0.34
* Tmin and Tavg has same +0.26 correlation with WnvPresent; Interestingly, DewPoint has the highest +0.31 with WnvPresent
* Windspeed features are relatively weakly correlated with both WnvPresent and NumMosquitos  
* Daily lags of temperatures offer some informative on autocorrelation up to a lag of five days while daily lag of 2 is the maximum for relative humidity  
* Station 1 and 2 data are empirically very similar. Due to the overwhelming number of missing values in Station 2, only Station 1 will be used for model feature selection.  
  
***3) EDA on Spray set***  

The sprays that were carried out in Chicago have been found to be largely reactive, irregular, inconsistent and ineffective.  

By using our model's recommendations on where, when, and how much to spray, Chicago needs only to rely on leading indicators that can be collected weeks and days in advance, enabling them to better plan and strategize their spray efforts.  

By computing their total sprayed areas in 2011 and 2013, and comparing them against our model's recommendations, we can quantify and evaluate different approaches for the most cost-effective method of spraying.  
  
***4) More EDA on Train plus Weather sets***  

This notebook goes into more details uncovering the relationships between the weekly time lags of various weather features and the `WnvPresent` and `NumMosquitos`.  

Different weather features have varying importances as to which weekly time lags are the strongest determinant for the mosquito party peaking in Jul-Aug. For instance, a 3-week time lag of `Tavg` was found to be the most important whereas a 4-5 week time lag of `StnPressure` appears to foreshadow the mosquito party.  

Using the `trap_cluster` feature that we have created in `EDA_Train_Test_Sets`, wherein each trap_cluster is segregated based on their total occurrences of `WnvPresent` over the four years, we can clearly identify strong weekly time lag features to explain the surge in `NumMosquitos` and `WnvPresent` during Jul-Aug.  

By grouping `Tavg` and `rh` features into various weather groups, we found that a 3-week time lags of `superHot_Dry`, `superHot_Wet`, `Hot_Dry`, and `Hot_Wet` were indeed largely accountable for the heavy spread of Wnv-carriers in the past four years.



### Model Selection Methodology  

The best features are selected based on how well they can explain the WNV-mosquitos surge patterns. All the selected features are leading indicators comprising of time-lagged features and two clustered features, `NumMosquitos_cluster` and `trap_cluster` which can be encoded beforehand with sufficient past data. This allows our best model to be not just predictive, but also highly anticipatory.  
  
The best model is selected based on its "true positive rate" or "recall rate".  
  
Models used for the binary classification problem includes:  
* LogisticRegression (best model)
* kNearestNeighbor
* BaggingClassifier
* RandomForestClassifier
* XGBoost
* AdaBoostClassifier
* VotingClassifier  


### Best Model Evaluation  

#### Logistic Regression Classification

The best model was found to be LogReg with a train/validation `area_under_curve` AUC score of around 0.81 and a test AUC score of 0.70. More pertinently, its Recall rate ("true positive rate") was found to be high at 0.78. Given an extremely imbalanced dataset where positive cases only constitues 5% of the entire dataset, being able to predict 78% of this small minority correctly is sufficiently strong to justify its use-case for deciding whether or not to spray. Having a high recall rate also means that the utility of spraying can be maximized resulting in a more cost-effective program.  
  
#### Model Coefficients Ranking

|Feature|Coefficient_exponentiated|
|:---|:---:|
|NumMosquitos_cluster|1.137201|
|month|1.114425|
|weekly_Tavg_lag_3|1.112479|
|weekly_Tavg_lag_2|1.104231|
|trap_cluster|1.093664|
|weekly_StnPressure_lag_4|1.089194|
|daily_Tavg_lag_2|1.087275|
|weekly_Tavg_lag_1|1.063897|
|weekly_StnPressure_lag_3|1.057296|
|daily_rh_lag_4|1.047616|
|superHot_Wet_lag_3|1.046634|
|daily_rh_lag_2|1.044773|
|Latitude|1.036143|
|Hot_Wet_lag_3|1.030259|
|weekly_StnPressure_lag_2|1.022086|
|superHot_Dry_lag_3|1.014562|
|weekly_precip_lag_3|0.978743|
|Hot_Dry_lag_3|0.964963|
|weekly_precip_lag_4|0.958408|
|Cool_Dry_lag_3|0.949527|
|Longitude|0.943808|
|superHot_Dry_lag_1|0.930454|
|Cool_Wet_lag_3|0.929885|

  
### Cost-Benefit Analysis (Case Study using 2013 data)
  
||Chicago's Spraying|With our Model|
|---|---|---|
|Number of Infected Human Cases|66<sup>#</sup>||15<sup>*</sup>|
|Average Medical Burden Cost per case (US$)<sup>1</sup>|21,000|21,000|
|**Total Medical Burden Costs (US$)**|**1,386,000**|**304,920**|
|Average Spray Cost per acre (US$)<sup>2</sup>|1.60|1.60|
|Total Spray(ed) Area, acres|60,234<sup>^</sup>|338,081|
|**Total Spray Costs (US$)**|**96,374**|**540,926**|
|**Total Costs (US$)<sup>3</sup>**|**1,483,000**|**846,000**|  
  
**_List of Assumptions:_**

<sup>#</sup>source: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7241786/  
  
<sup>*</sup>We assumed that the actual infected human cases could have been reduced proportionately by a factor of our Model’s recall rate of 0.78:  [(1-Recall rate) x Actual cases]

<sup>1</sup>According to a study published in the Journal of Infectious Diseases in 2014

<sup>2</sup>Assumed spray used is Larvicide which is less harmful to humans and environment and has a longer duration of 1-28 days depending on sunlight levels

<sup>3</sup>Total Costs=Total Medical Burden costs + Total Spray Costs

<sup>^</sup>Actual sprayed area is based on the spray data provided, added with an effective radial zone of 100meters from each spray point

  


### Conclusions and Recommendations

* Chicago's spraying program has been largely ineffective, irregular, inconsistent and reactive in nature.  
  
* Using our Best Model can allow them to better predict WHEN, WHERE, and HOW MUCH to spray    

* By using only leading indicators that are available weeks and days in advance, this will enable them to be proactive at predicting, planning, and preventing unnecessary WNV outbreaks. 