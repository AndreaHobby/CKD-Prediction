# Predicting Chronic Kidney Disease 
### Author: Andrea Hobby, MS

![kidney](img/fnalkidney-comp_1087848275.png)

## Table of Contents
1. [Background](#background)
2. [Goals](#goals)
3. [Data Collection and Data Cleaning](#DataCollectionandDataCleaning)
4. [Feature Selection](#FeatureSelection)
5. [Modeling](#modeling)
6. [Results](#Results)
7. [Final Thoughts](#FinalThoughts)
8. [Next Steps](#NextSteps)
9. [References](#References)
10. [Repo Structure](#repo)


<a name="background"/>

## Background
Chronic kidney disease (CKD) is when the kidneys are damaged and cannot correctly filter waste and excess fluids from the blood. About 37 million people in the United States have Chronic Kidney Disease (CKD). Early detection and diagnosis of CKD are essential to preventing its progression to kidney failure. Machine learning models can assist in predicting CKD. This project will use a decision tree to analyze National Center for Health Statistics (NCHS) data. Variables such as age, gender, medical history, and laboratory test results will be used. By identifying patterns in the data, models can predict a patient's risk of developing CKD, allowing for early intervention and management. 

<a name="goals"/>

## Goal(s)
- My goal for this analysis is to predict the risk of CKD. 
- Identify factors that increase the risk of CKD. 

<a name="DataCollectionandDataCleaning"/>

## Data Collection and Data Cleaning
The dataset was obtained from the National Center for Health Statistics (NCHS), consisting of 34 columns and 8819 rows. The data was collected from the National Health and Nutrition Examination Surveys conducted during the years 1999 to 2000 and 2001 to 2002. The dataset comprises information from adult participants who were 20 years of age or older.

Using the pandas library in Jupyter Notebook, the data was thoroughly examined. Variable types were checked, outliers and null values were identified, and duplicates and class imbalance were checked for. Since there was a class imbalance, random undersampling was applied to the dataset with a 1:1 ratio for targets to non-targets.

### Data science pipeline 
- Data
-- CSV File
- Processing
-- Jupyter Notebook
-- Pandas
-- NumPy
-- RandomUnderSampler
- Modeling
-- Sklearn
- Data Visualization
-- Matplotlib
-- Seaborn

<a name="FeatureSelection"/>

## Feature Selection

![corr](img/correlation%20matrix.png)


After reviewing the correlation matrix, I dropped the redundant variables like Weight and Height since we had BMI in the dataset. 

<a name="modeling"/>

## Modeling
After completing the exploratory data analysis, I concluded that a classification decision tree would best predict CKD. 

I performed hyperparameter tuning for a decision tree classifier using grid search with cross-validation. The hyperparameters to be tuned are the criterion for splitting, the maximum depth of the tree, and the minimum number of samples required to split an internal node. I used a dictionary to specify a range of values for each hyperparameter.

I created an instance of the decision tree classifier and performed a grid search with cross-validation using the specified hyperparameters and the training set. The best hyperparameters are selected based on the highest mean score across all cross-validation folds.

_Best hyperparameters:  {'criterion': 'gini', 'max_depth': 2, 'min_samples_split': 2}_

I created another instance of the decision tree classifier with the best hyperparameters, and the model is trained on the training set. I then used the resulting model to make predictions on the testing set.


<a name="Results"/>

## Results
### Decision Tree Performance:
- Accuracy: 0.7033898305084746
- Precision: 0.6551724137931034
- Recall: 0.7169811320754716
- F1 Score: 0.6846846846846846

### Random Forest Performance:
- Accuracy: 0.7711864406779662
- Precision: 0.7321428571428571
- Recall: 0.7735849056603774
- F1 Score: 0.7522935779816513

### Gradient Boosting Performance:
- Accuracy: 0.8050847457627118
- Precision: 0.7678571428571429
- Recall: 0.8113207547169812
- F1 Score: 0.7889908256880735



<a name="FinalThoughts"/>

## Final Thoughts
Since I chose to create categorical variables from some of the continuous variables, it is possible that I lost some information and decreased accuracy. 
Also, I dropped missing values for this analysis, but I would consider imputing the missing data next time. 

<a name="NextSteps"/>

## Next Steps
- Combine this with another dataset for a more robust analysis or try machine learning algorithms like logistic regression or a neural network for the next steps. 
- Build a web app using streamlit with a user interface for this model. 

<a name="References"/>

## References
Kidney Disease Statistics for the United States. National Institute of Diabetes and Digestive and Kidney Diseases. U.S. Department of Health and Human Services. Available at: https://www.niddk.nih.gov/health-information/health-statistics/kidney-disease (Accessed: February 22, 2023). 

<a name="repo"/>

## Repo Structure
```
├── /data (data)
├── /img (contains all images for repo)
├── Predicting Chronic Kidney Disease.ipynb
└── README.md

