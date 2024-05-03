![](https://github.com/UTA-DataScience/ProjectTempate/blob/main/UTA-DataScience-Logo.png)

**Joshua A. Ruiz**  
jar3654@mavs.uta.edu  

# Breast Cancer Kaggle Project

This repository is for an attempt on the WiDs Datathon 2024 Challenge #1. 

## Overview

In this kaggle challenge the goal is to be able to predict breat cancer in women, and to accomplish this we will need to:

  + 1.) Go over the data and clean it up.

  + 2.) Make a model that can accuratly predict cancer possibilities based on data information.

Our code was made with these 2 objectives in mind and my model achieved accuracy ratings roughly ~ 60% across the board, in which the example solution set only got 50%. 

## Summary of Work done
### Data

#### Preprocessing

When looking at the raw data itself we could see that the main issues come from missing data values, and strings instead of numbers.
So we did several things that make it better for our model prediction:

  + 1.) Since race had over 8000 out of 12000 entries missing values, we excluded it out of the model due to the impact it would have, and we also excluded patents:
    + Zipcode, ID, Insurance type, all the codes for breast cancer types and codes associated with them (since we already have a column dedicated for a yes/no cancer detection)
  + 2.) For the remaining tables, since they had very little missing data values we removed the rows from the data since they were less than 2% of the data.

#### Data Visualization
Since

### Training

### Performance Comparison

## Conclusions

# How to reproduce results

## Overview of files in repository

## Software Setup

## Data

### Performance Evauluation

# Citations
