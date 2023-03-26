# Phase 3 Project
**Client:** Providence (Most medical centers) <br>
**Authors:** Tommy Phung 

## Overview
According to the [CDC](https://www.cdc.gov/flu/prevent/vaxsupply.htm#:~:text=Flu%20vaccine%20is%20produced%20by,for%20the%202022%2D2023%20season.), there is a projected supply of over 170 million influenza vaccines throughout the United States. 

Many hospitals do not keep track of the number of vaccines they waste. History shows that vaccines are unused as well. An estimated 71 million H1N1 flu vaccines were unused, and an estimated 1.1 billion Covid Vaccines went to waste due to expired vaccines and supply chain issues.** <br>

With the growing doubts about vaccine effectiveness, patients have been questioning whether to take the Covid-19 vaccine. We used the National 2009 H1N1 Flu Survey provided by [United States National Center for Health Statistics](https://www.cdc.gov/nchs/index.htm) for our dataset. We will be modeling to see if we can predict whether an individual has taken the Seasonal Vaccine based on several different features from their responses in the survey. Using the model, a medical center can have a rough idea of the number of vaccines needed. 

Three models were created using decision trees and random forest algorithms. <br>
**The Decision tree** was used as a baseline model in order to find improvements. Little to no changes were made to the parameters. <br>
**The Random Forest** was the solution to the decision tree's initial problems. The model was an improvement to the baseline but could be better if tuned for the best accuracy. <br>
Lastly, the **Tuned Random Forest** to find the best combinations of parameters for the model. Multiple combination were look through using **Gridsearch.**  <br> 
The model progressively improves the training and testing accuracy in order to predict the patient's vaccine status. 

## Business Understanding 
Vaccines are a useful way to prevent viral infections. One of the most common viral infections is influenza or most commonly known as the flu. The CDC recommends individuals receive the vaccine during the flu season every year. However, since vaccines aren't mandatory, individuals can deny them through personal beliefs or limited knowledge of the vaccine. When vaccines go unused, they are wasted in the center rather than distributed to centers needed. <br> 

**The vaccines could have been distributed to areas with inadequate number of vaccines.**

**For example, 1.1 billion Covid Vaccines were estimated to be wasted due to expired vaccines and supply chain issues.** <br>

To give patients the vaccines as efficiently as possible, hospitals and medical centers store vaccines. With the dataset, we could predict whether a patient would want a vaccine based on their answers to the survey. Medical centers can then order an adequate amount of vaccines with little waste. 

## Data Understanding
The dataset consists of binary and numerical entries based on their answers to a survey. To model the dataset, all of the data types need to be numeric so dummy variables are needed for 12 of the columns. After the dummy variables were made, there are over 100 different columns created and will be used in the modeling. We looked at **accuracy** and **recall** scores to see how well the model performs and if a higher recall score can lead to a better resulting model. The accuracy score is used to gauge how well the model performs. The recall score will be used to give certainty that the patient who needs the vaccines will receive one. 

The following is a graph with all the features from the survey as well as a description of the label. 

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
| chronic_med_condition       | Has a chronic medical condition |
| child_under_6_months        | Has regular close contact with a child under the age of six months                                                                  |
| health_worker               | Is a healthcare worker                                                                                                                                                                                                                                                                                                                           |
| health_insurance          | Has health insurance                                                                                                                                                                                                                                                                                                                               |
| opinion_h1n1_vacc_effective | Respondent's opinion about H1N1 vaccine effectiveness                                                                                                                                                                                                                                                                                           |
| opinion_h1n1_risk           | Respondent's opinion about the risk of getting sick with H1N1 flu without vaccine                                                                                                                                                                                                                                                                   |
| opinion_h1n1_sick_from_vacc | Respondent's worry about getting sick from taking the H1N1 vaccine                                                                                                                                                                                                                                                                                     |
| opinion_seas_vacc_effective | Respondent's opinion about seasonal flu vaccine effectiveness                                                                                                                                                                                                                                                                                   |
| opinion_seas_risk           | Respondent's opinion about the risk of getting sick with seasonal flu without vaccine                                                                                                                                                                                                                                                               |
| opinion_seas_sick_from_vacc | Respondent's worry of getting sick from taking seasonal flu vaccine                                                                                                                                                                                                                                                                             |
| age_group                   | Age group of respondent                                                                                                                                                                                                                                                                                                                         |
| education                   | Self-reported education level                                                                                                                                                                                                                                                                                                                   |
| race                        | Race of respondent                                                                                                                                                                                                                                                                                                                               |
| sex                         | Sex of respondent                                                                                                                                                                                                                                                                                                                               |
| income_poverty              | Household annual income of respondents to 2008 Census poverty thresholds                                                                                                                                                                                                                                                             |
| marital_status              | Marital status of respondent                                                                                                                                                                                                                                                                                                                     |
| rent_or_own                 | Housing situation of the respondent.                                                                                                                                                                                                                                                                                                                 |
| employment_status           | Employment status of the respondent.                                                                                                                                                                                                                                                                                                                 |
| hhs_geo_region              | Respondent's residence using a 10-region geographic classification defined by the U.S. Dept. of Health and Human Services.                                                                                                                                         
| census_msa                  | Respondent's residence within metropolitan statistical areas (MSA) as defined by the U.S. Census                                                                                                                                                                                                                                                 |
| household_adults            | Number of other adults in the household, top-coded to 3                                                                                                                                                                                                                                                                                             |
| household_children          | Number of children in household, top-coded to 3                                                                                                                                                                                                                                                                                                 |
| employment_industry         | Type of industry respondent is employed in. Values are represented as short random character strings                                                                                                                                                                                                                                             |
| employment_occupation       | Type of occupation of the respondent. Values are represented as short random character strings                                                                                                                                                                                                                                                       |

***<p style="text-align: center;">Targets</p>***

| Label            | Description                                      |
|------------------|--------------------------------------------------:|
| h1n1_vaccine     | Whether respondent received H1N1 flu vaccine     |
| seasonal_vaccine | Whether respondent received seasonal flu vaccine |

For this model, we will be focusing on the **season flu vaccine** label from the dataset.

## Method 
Preprocessing steps are filling in missing data, and dummy variables being created and scaled with a scaler. I used weight random choice to fill in the missing values to utilize as much of the dataset as possible. Dummy variables are used as well to deal with the categorical data and the MinMax scaler was used to scaler the data from 0 to 1. 

We will be using a machine learning algorithm to help us predict whether a patient will take the vaccine. Unlike simple data analysis, machine learning is used on a complex dataset where we have several, in this case, over 100 different features to help predict the target variable. I used a decision tree and random forest machine learning algorithm.
We need to perform multiple classification models to help predict the targeted variable, seasonal vaccines. 

There are 3 models created: 
1. **Decision Tree** <br>
Default parameters are used to be used as a baseline to look for what needs to be performed.
2. **Random Forest** <br>
The majority of the parameters are default but some were changed to improve from the previous model 
3. **Random Forest with tuned hyperparameters** <br>
By using GridSearch, a dictionary of a list of parameters is scoped to see which parameters would lead to the best results. 

We will be looking at the accuracy to see how accurate the model performs on the training dataset and the testing dataset. Another measurement to keep in mind was the recall score. 

## Results 
| Model | Training Accuracy | Testing Accuracy | Recall Score  |                                                                                     
|:------|:-------------:|:------------:|:--:|
| Decison Tree | 100% | 68.21% | 65.33% |
| Random Forest| 83.45%| 77.89% | 75.55% |
| Random Forest with Tuning| 92.59% | 78.36%|75.55%|

## Evaluation
### Decision Tree
The Decision Tree model had a **100%** accuracy when predicting with the training dataset with a **68.21%** accuracy score with the testing dataset. When the accuracies have a large difference, this is a sign of overfitting. This is because decision trees perform a greedy algorithm and will always result in the same model.  

**Solution:** Reduce the max depth or use a model that isn't prone to overfitting. In this case, a **Random Forest** was used for the next model. 

### Random Forest
The Random Forest was set with a max depth and no restriction to the max amount of features similar to parameters as the decision tree. Random Forest builds upon decision trees made up of an ensemble of trees voting on the results. The Random Forest model had an **83.45%** accuracy on the training dataset and an **77.89%** accuracy score on the testing dataset. Although the training accuracy decreased from the decision tree, the testing accuracy increased instead. This model was not overfitted but the parameters were given to mirror the decision tree default parameters. 

**Solution:** To improve the model, **GridSearch** was used to search through the different hyperparameters to find the best-performing parameters. A directory of parameters was searched to find the best combination of parameters for the random forest model to obtain the best accuracy. 

### Tuned Random Forest
The best parameters from the list, was found with GridSearch with the scoring to the best accuacy. This model has an training accuracy score of **92.59%** and a testing accuracy score of **78.36%**. There was an improvement with the testing accuracy which means that the parameters used was better than the parameters given before. Recall score stayed the say meaning that the model is correctly predicting the number of patient taking the vaccines. 

## Example
| Classifier | Number of Patients |Prediction| True Prediction | Supply of Vaccine | Wasted Vaccines |                                                                                     
|:----:|:------:|:-------------:|:------------:|:----:|:---:|
|Decision Tree| 5342 | 2455| 2466 | 2578 | 112 | 
|Random Forest| - | 2441| - | 2563 | 97 | 
|Tuned Random Forest | - | **2416**| - | **2537** | **71** | 

## Conclusion
The decision tree classifier performs well on the training dataset but not on the testing dataset. To resolve that, a random forest is used instead to prevent the model from overfitting the dataset when fitted. However, given a large number of combinations of parameters, **GridSearch was used to find the best-performing combination for the Random Forest Model**. Although the model only had an accuracy of roughly **80%**, that will be good enough to allow medical centers to order a reasonable amount of vaccines when the model predicts a respondent's willingness to take the vaccine. With a good enough recall score and extra vaccines, we can minimize the number of vaccines wasted. With **5% extra vaccines supplied**, there was only a waste of under 100 vaccines compared to expecting everyone to be taking the vaccines. 

## Limitations
Unfortunately, there is a large combination of parameters that the classifier can use to make the best model and it is too computationally complex to look through and compare which has the best performance. That is why only a list of parameters was given to save time and narrow down the best combination. There could be an instance where a specific model performs better with the training set but not the testing set or vice versa. If given time, there could be the best-performing model for a given state but would be unrealistic to obtain a prediction. 
1. **Majority of the questions are targeted toward the H1N1 vaccines which don't reflect too well if they were to take the seasonal vaccine.** <br>
The question could become irrelavent if the vaccines aren't needed or in the public mind such as the polio vaccine, which for the most part is elimated. 
2. **New generations and events may affect people's willingness to take the vaccines.** <br>
Covid-19 has had an impact on people's perception of vaccines, either good or bad. Along with other factors such as religion, people's opinions will change which can make the model ineffective if not updated for the new population. 

## Recommendations
1. Given time, I would recommend exploring **different classification models** and **different combinations** of parameters to improve the model. <br>
Ideally, an 80% would be preferred but not as needed since a medical center should have a range of vaccines supply to take into account situations such as new patients. <br>
2. **Modified or targeted questions** should be added to the survey. <br>
The survey was made asking primarily about the H1N1 virus and could be changed to adapt to the current state of the world such as covid-19. <br>
3. Determine an **adequate amount** of spare vaccines to allocate from one center to another. <br>
Not all medical centers will have the same results and should be treated regionally to maximize the accuracy of the model. For example, I added an extra 5% more vaccines but could be different from city to city. <br>

## Repository Structure
```
├── README.md                           <- The top-level README for reviewers of this project
├── house_notebook.ipynb                <- Narrative documentation of analysis in Jupyter notebook
├── presentation_3.pdf                  <- PDF version of project presentation
├── pictures                            <- Graphs and plots created by code
├── modeling_code.ipynb                 <- GridSearch that was excluded out the code
└── Data                                <- Original dataset from Website
```
