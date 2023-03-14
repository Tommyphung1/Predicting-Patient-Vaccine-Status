# Phase 3 Project
**Client:** Providence (Most medical centers) <br>
**Authors:** Tommy Phung 


## Overview
With the growing doubts on vaccines effectivness, patients are questoning whether to take the Covid vaccine. We will be using the National 2009 H1N1 Flu Survey provided from [United States National Center for Health Statistics](https://www.cdc.gov/nchs/index.htm). We will be modeling to see if we can predict whether an individual have taken the Seasonal Vaccine based on several different features from the their response in the survey. Using these prediction, a medical center can have a rough estimate on how many vaccines are needed during a given season. This model needs to be accurate enough so that vaccines aren't being wasted in areas not needed. 



The Following is a graph with all the features from the survey as well a description of the label. 

***<p style="text-align: center;">Features</p>***


| Label                       | Description                                                                                                                                                                                                                                                                                                                                     |
|:-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| h1n1_concern                | Level of concern about the H1N1 flu                                                                                                                                                                                                                                                                                                             |
| h1n1_knowledge              | Level of knowledge about H1N1 flu                                                                                                                                                                                                                                                                                                               |
| behavioral_antiviral_meds   | Has taken antiviral medications                                                                                                                                                                                                                                                                                                                 |
| behavioral_avoidance        | Has avoided close contact with others with flu-like symptoms                                                                                                                                                                                                                                                                                     |
| behavioral_face_mask        | Has bought a face mask                                                                                                                                                                                                                                                                                                                           |
| behavioral_wash_hands       | Has frequently washed hands or used hand sanitizer                                                                                                                                                                                                                                                                                               |
| behavioral_large_gatherings | Has reduced time at large gatherings                                                                                                                                                                                                                                                                                                             |
| behavioral_outside_home     | Has reduced contact with people outside of own household                                                                                                                                                                                                                                                                                         |
| behavioral_touch_face       | Has avoided touching eyes, nose, or mouth                                                                                                                                                                                                                                                                                                       |
| doctor_recc_h1n1            | H1N1 flu vaccine was recommended by doctor                                                                                                                                                                                                                                                                                                       |
| doctor_recc_seasonal        | Seasonal flu vaccine was recommended by doctor                                                                                                                                                                                                                                                                                                   |
| chronic_med_condition       | Has a chronic medical conditions |
| child_under_6_months        | Has regular close contact with a child under the age of six months                                                                  |
| health_worker               | Is a healthcare worker                                                                                                                                                                                                                                                                                                                           |
| health_insurance          | Has health insurance                                                                                                                                                                                                                                                                                                                               |
| opinion_h1n1_vacc_effective | Respondent's opinion about H1N1 vaccine effectiveness                                                                                                                                                                                                                                                                                           |
| opinion_h1n1_risk           | Respondent's opinion about risk of getting sick with H1N1 flu without vaccine                                                                                                                                                                                                                                                                   |
| opinion_h1n1_sick_from_vacc | Respondent's worry of getting sick from taking H1N1 vaccine                                                                                                                                                                                                                                                                                     |
| opinion_seas_vacc_effective | Respondent's opinion about seasonal flu vaccine effectiveness                                                                                                                                                                                                                                                                                   |
| opinion_seas_risk           | Respondent's opinion about risk of getting sick with seasonal flu without vaccine                                                                                                                                                                                                                                                               |
| opinion_seas_sick_from_vacc | Respondent's worry of getting sick from taking seasonal flu vaccine                                                                                                                                                                                                                                                                             |
| age_group                   | Age group of respondent                                                                                                                                                                                                                                                                                                                         |
| education                   | Self-reported education level                                                                                                                                                                                                                                                                                                                   |
| race                        | Race of respondent                                                                                                                                                                                                                                                                                                                               |
| sex                         | Sex of respondent                                                                                                                                                                                                                                                                                                                               |
| income_poverty              | Household annual income of respondent with respect to 2008 Census poverty thresholds                                                                                                                                                                                                                                                             |
| marital_status              | Marital status of respondent                                                                                                                                                                                                                                                                                                                     |
| rent_or_own                 | Housing situation of respondent.                                                                                                                                                                                                                                                                                                                 |
| employment_status           | Employment status of respondent.                                                                                                                                                                                                                                                                                                                 |
| hhs_geo_region              | Respondent's residence using a 10-region geographic classification defined by the U.S. Dept. of Health and Human Services.                                                                                                                                         
| census_msa                  | Respondent's residence within metropolitan statistical areas (MSA) as defined by the U.S. Census                                                                                                                                                                                                                                                 |
| household_adults            | Number of other adults in household, top-coded to 3                                                                                                                                                                                                                                                                                             |
| household_children          | Number of children in household, top-coded to 3                                                                                                                                                                                                                                                                                                 |
| employment_industry         | Type of industry respondent is employed in. Values are represented as short random character strings                                                                                                                                                                                                                                             |
| employment_occupation       | Type of occupation of respondent. Values are represented as short random character strings                                                                                                                                                                                                                                                       |


***<p style="text-align: center;">Targets</p>***

| Label            | Description                                      |
|------------------|--------------------------------------------------:|
| h1n1_vaccine     | Whether respondent received H1N1 flu vaccine     |
| seasonal_vaccine | Whether respondent received seasonal flu vaccine |

For this model, we will be focusing the **season flu vaccine** label from the dataset.

## Business Understanding 
Vaccines are a useful way to prevent viral infections. One of the most common viral infections is influenza or most commonly known as the flu. The CDC recommended individuals to recieve the vaccine during the flu season of every year. However, since vaccines aren't manditory, individuals may deny them through personal beliefs or limited knowledge of the vaccine. Vaccines would be wasted where they could be used in other medical centers. <br> 

**For example, 1.1 billion Covid Vaccines were estimated to be wasted due to expired vaccines and supply chain issues.** <br>

In order to give patients the the vaccines as efficently as possible, hospitals and medical center store vaccines to be administer quickly whenever requested. With the current dataset, we could potentially predict whether a patient would want a vaccine based on their answers on the survey. This way, medical center can order an adiquite amount of vaccines with minimual waste. 

## Data Understanding
The dataset consist of binary and numerical entries based on their answers on a survey. There are 8 columns that have 5% of the data missing that were determined to be the cutoff to be removed. The remaining data will be filled with the approprate measurements. In order to model the dataset, all of the data type needs to be a numeric so dummy variables are needed for 12 of the columns. 

## Method 
We need to perfrom multiple claffication models to help predict the targeted variable, seasonal vaccines. 
There will be 3 models: 
1. Decision Tree <br>
Default parameters are used to be used as a baseline to look for what needs to be perfomed.
2. Random Forest <br>
Majority of the parameters are default but some were changed to improve from the previous model 
3. Random Forest with tuned hyperparameters <br>
By using GridSearch, a dictionary of list of parameters are scoped to see which parameters would lead to the best results. 

We will be looking at the accuracy to see how accurate the model perform on the training dataset and the testing dataset. 

There were missing values and I was uncertain which method would be best. <br>
1. The first attempt removed **columns** with more than 5% missing values.
2. The second attempt was to remove the **indexs** or particiants that have missing values. <br>
3. The final attempt created weight probability for each columns and **randomly** give each missing value for each columns. <br>

## Results 


