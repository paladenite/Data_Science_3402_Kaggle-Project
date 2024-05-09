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

Before preprocessing the data, when looking at the raw csv format, automatically at a first glance you can see that the vast majority of the data has nothing to do with cancer. However, we can still make use from BMI, Age, and NO2 as natural indicators of cancer as the higher the BMI, higher the Age, and the more NO2 gasses there are, the chance of cancer in general increases significantly. Outside of the natural indicators, we can also use the diagnosis codes for both breast and metastatic cancer as a good indicator from the doctors first prognosis. We can also use Race to see if a particular group is more susceptible to cancer, and payer_type as a good indicator for an individuals wealth status to see if financial causes lead up to cancer as well.

#### Preprocessing

Due to the high amounts of missing data for Race and BMI we cannot supplement data into those columns as it will heavily affect the result, so unfortunately they will be droped and since the remaining null values are small in number, less than 1% of the data, we can drop those entries as well. 

![image](https://github.com/paladenite/Data_Science_3402_Kaggle-Project/assets/112378770/41673e61-9ae0-4e0a-a478-71bc6572f63b)

For the remaining columns, we must make sure that they are all floats and so payer_type, breast and metastatic cancer codes will all be hard encoded to help with data processing and identification of causes. 

### Data Visualization

When using statistical data distributions overlayed with the data distributions we can see a clear overlap in our data which means that we do not have to worry about outside unknown factors messing with our data set and dont have to compensate for much.

![download](https://github.com/paladenite/Data_Science_3402_Kaggle-Project/assets/112378770/04a2f61e-ef76-49b2-b030-257d79d43a84)


### Model Training and Performance Comparison

All the models trained were primarily ensemble methods and stackings of those methods. As said before 72% of our data set was set for training the model and 28% was for testing. The exact percentage was determined from playing around with the test_size hyperparameter with all the models, and all of them performed higher at that mark.

The first one was a model that primarily used the Random Forest method.

![download](https://github.com/paladenite/Data_Science_3402_Kaggle-Project/assets/112378770/b13ce6a3-69f3-4301-b9e3-388390d2ac1b)

From here I stacked it with an XGBoost to help with any extreme gradients that may be affecting it.

![download](https://github.com/paladenite/Data_Science_3402_Kaggle-Project/assets/112378770/458353c2-411f-4482-b630-96cfdfbbcd43)

Since the score didnt improve much I decided for a much milder approach and used only Gradient Boosting.

![download](https://github.com/paladenite/Data_Science_3402_Kaggle-Project/assets/112378770/d653e81f-cf3e-4447-9e15-87a910b7043c)

However the scoore didnt improve by much either. So I went back and did AdaBoosting with XGBoosting.

![download](https://github.com/paladenite/Data_Science_3402_Kaggle-Project/assets/112378770/8ce60f09-934a-4dee-bdb8-c34e0df2b23b)

From here I did a Cross Validation against Random Forest, Gradient Boosting, and XGBoosting. I left AdaBoosting out since it did nearly the same as Forest with XGBoost.

![download](https://github.com/paladenite/Data_Science_3402_Kaggle-Project/assets/112378770/86fbb798-eb52-4eca-b1d4-6131054fa94f)

The models would have performed much better if we had BMI involved since BMI is one of the strongest factors to an onset of cancer. Race may have also helped due to different ethnic diets and genetic dispositions, but since both were dropped the accuracy that we get Is quite good. 

However when doing the submission for the kaggle project the model i used was the gradient boost since it had the highest accuracy. It, however, only got a score of  0.742 which may tell us that our models were cusping on the edge of overfitting because of the accuracy drop. However It doesnt help that we had around 500 out of around 5500 missing predictions due to the entries being cut due to missing varibles. Which had to be replace in order to submit the data to be graded. Otherwise I think our accuracy would be higher but most likely wouldnt reach 79%.

![download](https://github.com/paladenite/Data_Science_3402_Kaggle-Project/assets/112378770/735b3078-0cfa-44ab-be6c-78e563f25e96)

## Conclusions

Despite the huge amount of data we gotten, less than 3/4ths of it was not applicable to the problem, and a significant portion of that remaining data had to be chunked due to vasts amounts of missing entries. Despite this, using the remaining data it is apparant that, while much more optimization with the models and experimenting with different stacks can lead to a higher score of accuracy, it seems that it plataues near 80% and not much more can be achieved without more data.

## Data

The data and the challenge itself can be found [here](https://www.kaggle.com/competitions/widsdatathon2024-challenge1/data)
