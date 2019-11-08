# Drinking Water: Predicting quality violations in New England

The US Environmental Protection Agency (EPA) sets standards for drinking water quality and is responsible for implementation of the Safe Water Drinking Act (SWDA). Annually, numerous water systems detect contaminants above the Maximum Contaminant Level (MCL), for instance 3 to 10% of the _community water systems_ (c.f. [Allaire 2018](https://www.pnas.org/content/115/9/2078)). The drinking water quality violations can be tragic for the served communities. Can we predict their occurrences? Local agencies collect water samples and send them to the EPA in case of any violation. The EPA store and share this data in the Safe Drinking Water Information System ([SDWIS](https://www.epa.gov/enviro/sdwis-model)).

In this project, I ask: **How predictable are drinking water violations in water systems?**

* Which factors are good predictors?

* Is using only SDWIS data sufficient?

* How predictable are specific types of violations? I will focus on pesticides, because their is a clear causal relationship between pesticide use in crops and pesticide contaminations in drinking water.

The aim is to predict which water systems are likely to be subject to violations of water quality in a given year for New England. The task is a binary classification of water systems:  
0. not likely to have a violation of the drinking water quality this year
1. likely to have a violation of the drinking water quality this year

The classifier is trained on data from 2013 to 2015, validated on data from 2016 and tested on water quality data from 2017. I will favor explanatory approach.  

I complement the SDWIS data with estimated pesticide use by county ([NAWQA](https://water.usgs.gov/nawqa/pnsp/usage/maps/county-level/)), and build two models:  
A. Outcome variable is had any violation
B. Outcome variable is had any pesticide violation

### Conclusion

SDWIS data is not sufficient to predict drinking water quality violations, as it contains few features that are correlated violations occurrences. The performance of the classifier was poor. The most important features to predict the violations (model A) are:  
1. previous occurrences
2. estimated pesticide use
3. size of the water system

Too few violations due to the presence of presticides in the drinking water occurred in New England to run any model (model B).   

My recommendations are thus that any model trying to predict drinking water quality violations, in order to be successful, should focus on one particular type of violation and complement SDWIS with external contextual data. The model will always be limited by the granularity of the data collection by the EPA (quarterly sampling).  

Ideas of external data sources that can be added are: census data, particularly average income as it is known that poorer communities have more difficulties to maintain their costly water system, and weather data as water run-off are one major cause of water contaminations.  

In short, the current model could be used to build a risk exposure map by county of the likelihood of water quality violations occurrences, but it will not be able to predict future violations.  

### Techniques and Python Packages Used

In this project, I could use and train my skills in: supervised learning, data processing and feature engineering, L2 logistic regression, gradient boosting, random forest, reading REST APIs, cross-validation, parameter tuning, classification evaluation metrics, handling of class-imbalance. I used notably those python packages and functions: scikit-learn, pandas, requests, GridSearchCV, SMOTE.  

**The procedure and results are summarized in [this presentation](https://docs.google.com/presentation/d/1_BFCSApEwgKDsnK_6E4I5ZDO8wfYpLv-QmWbZlTdxt4/edit?usp=sharing)**, also found below.

## Code

The data is coming from SDWIS, all the extraction is described in [this notebook](https://github.com/de-la-viz/pesticides_in_drinking_water/blob/master/code/Data_Extraction.ipynb). Pesticide use estimates are downloaded from the National Water-Quality Assessment ([NAWQA](https://water.usgs.gov/nawqa/pnsp/usage/maps/county-level/)) Project. Data processing is done and explained in [this notebook](https://github.com/de-la-viz/pesticides_in_drinking_water/blob/master/code/Data_Processing_and_Feature_Engineering.ipynb). The classification and prediction is done in [this notebook](https://github.com/de-la-viz/pesticides_in_drinking_water/blob/master/code/Classification.ipynb).

## Slides

![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(1).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(2).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(3).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(4).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(5).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(6).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(7).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(8).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(9).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(10).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(11).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(12).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(13).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(14).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(15).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(16).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(17).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(18).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(19).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(20).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(21).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(22).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(23).png)
![img](documents/slides%20as%20png/Predicting%20Drinking%20Water%20Quality%20Violations%20in%20New%20England%20(24).png)
