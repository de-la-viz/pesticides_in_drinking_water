# Pesticides in Drinking Water
A try at predicting violations of maximum contaminant levels in US drinking water by pesticides.

## Strategy

### Data Extraction

* Directly from SDWIS using their API
* Water_System and Violations tables, merge by PWSID
* Select a First a few number of features that seem to be relevant
* Filter the violations to get only the/some pesticides
* Focus on New England (EPA region 1), to reduce amount of data
* 2009-2018
* Download [Estimate Use of Pesticides by County](https://water.usgs.gov/nawqa/pnsp/usage/maps/county-level/)
* Merge pesticide use to drinking water violations by [matching counties and ZIP codes](https://wonder.cdc.gov/wonder/sci_data/codes/fips/type_txt/cntyxref.asp)
* Final dataset is one line per water system, summing pesticides MCLs violations (or binarized), evtl. with dummy for the contaminants.

### Feature Selection and Engineering

* Select a First a few number of features that seem to be relevant
* add dummies for year, quarter
* add neighboring water systems, if previous violations in them
* add column with pesticide use by ZIP (water system)
* verify that there is a minimum of correlation with outcome

### Handling Class Imbalance

* instead of accuracy, use precision or recall
* oversample minority class or undersample majority class?
* Try SMOTE - Synthetic Minority Over-sampling Technique?
* Look and be inspired by kaggle _credit card fraud detection_. How did they handle class imbalance? Look at the kernels people have uploaded.

### Training and Model Selection

* train on 2006-2016
* validate on 2017
* test on 2018
* try logistic regression and gradient boosting, as can see what features are most relevant
* use gridsearchCV
* second-step of feature selection?

