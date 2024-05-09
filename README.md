![](https://github.com/UTA-DataScience/ProjectTempate/blob/main/UTA-DataScience-Logo.png)

**Joshua A. Ruiz**  
jar3654@mavs.uta.edu  

# Breast Cancer Kaggle Project

This repository is for an attempt on the WiDs Datathon 2024 Challenge #1. 

## Overview

In this kaggle challenge the goal is to be able to predict breat cancer in women. The dataset, sourced from Health Verity, has been enhanced with additional geo-demographic data from third-party sources. This dataset hopefully offers insights into socio-economic factors impacting health equity. By integrating census data and other socio-economic indicators, it helps identify healthcare disparities and informs targeted interventions for promoting health equity. From this dataset we are asked to predict if the patients received metastatic cancer diagnosis, and to accomplish this we will need to:

  + 1.) Go over the data, do a bit of real world analysis of the relationships the data collected have with our goal.

  + 2.) Clean up, do feature engineering if needed, and normalize or edit the data as needed.
    
  + 3.) Make various models that can accuratly predict cancer possibilities based on data information that we chosen and tweak it to get our desired results.

With these objectives in mind, the best model I managed to create obtain a 74.2% accuracy prediction rate using Gradient Boosting.

## Summary of Work done
### Data

The data set itself had 12908 entries for training the model and testing the model. 72% of the entries will be used for training, and the remaining 28% for testing.

Before preprocessing the data, when looking at the raw csv format, automatically at a first glance you can see that the vast majority of the data has nothing to do with cancer. However, we can still make use from BMI, Age, and NO2 as natural indicators of cancer as the higher the BMI, higher the Age, and the more NO2 gasses there are, the chance of cancer in general increases significantly. Outside of the natural indicators, we can also use the diagnosis codes for both breast and metastatic cancer as a good indicator from the doctors first prognosis.

#### Preprocessing

![image](https://github.com/paladenite/Data_Science_3402_Kaggle-Project/assets/112378770/41673e61-9ae0-4e0a-a478-71bc6572f63b)


  + 1.) Since race had over 8000 out of 12000 entries missing values, we excluded it out of the model due to the impact it would have, and we also excluded patents:
    + Zipcode, ID, Insurance type, all the codes for breast cancer types and codes associated with them (since we already have a column dedicated for a yes/no cancer detection)
  + 2.) For the remaining tables, since they had very little missing data values we removed the rows from the data since they were less than 2% of the data.


### Data Visualization

### Model Training and Performance Comparison

The 4 models I trained were a Logistical Regressions, and a Random Forrest, out of the four different models all of them failed,they were oversaturated with data that should have been seperated. Because data from location, income, age, and air quality were mixed together, they couldn't get accurate results from them.

## Conclusions

What we could have done better was chunk the data into several classifications as there was atmosphere gasses, income levels, etc. As making one model to handle it all was a bit much and end the end with an AUC score so below it shows it. Classifications should help with the data by seperating revelent/related data into seperate files and help alot more

## Data

The data and the challenge itself can be found [here](https://www.kaggle.com/competitions/widsdatathon2024-challenge1/data)
