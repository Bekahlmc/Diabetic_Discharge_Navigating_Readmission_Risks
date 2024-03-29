# Diabetic_Discharge_Navigating_Readmission_Risks

#### Bekah McLaughlin

<p align="center">
  <img src = ./Images/pexels-mart-production-7089401.jpg>
</p> 

## Overview

VitalCare Health Syste is aiming to reduce early readmission rates among diabetic patients to improve overall patient outcomes. To achieve this goal, an analysis will be conducted on a comprehensive dataset about hospitalized diabetic patients and whether they were readmitted within 30 days of discharge.

Tracking and mitigating readmission rates within 30 days of discharge serves as a critical key performance indicator for hospitals for two main reasons:

1. Firstly, an early readmission, occurring within 30 days of discharge, signals potential gaps in care that weren't addressed prior to the patient's discharge. These gaps elevate the risk of poorer patient outcomes, underlining the importance of comprehensive care continuity.

2. Secondly, early readmissions within this timeframe can cause significant financial burdens on hospitals. In addition to this, hospitals often receive only partial reimbursement from insurance providers for early readmissions.

### **The Dataset**

The dataset includes a decade's worth of US hospital data spanning from 1999 to 2008, with over 100,000 entries, each representing a patient's hospitalization and associated details. The target is `'readmission'`. It has more than 50 features, including demographic information such as:
- age group
- gender
- race

Alongside medical specifics such as:
- diagnoses
- medications prescribed
- number of procedures during hospitalization
- other pertinent details regarding the patient's stay.

For a full description and download of the dataset, click <a href = "https://archive.ics.uci.edu/dataset/296/diabetes+130-us+hospitals+for+years+1999-2008">here</a>. Also, a full descripton of each feature label is in the Data folder.

### **The Goal**

The goal of this project is to use the dataset to develop a model capable of accurately identifying patients who are at risk of being readmitted within 30 days of discharge.

## Data Understanding and Visualization

After initial cleaning, 70815 rows and 20 columns remained, including the target.

<p align="center">
  <img src = ./Images/cateda1.png>
</p> 

<p align="center">
  <img src = ./Images/cateda2.png>
</p> 

<p align="center">
  <img src = ./Images/cateda3.png>
</p> 

### **Categorical Feature Chi-Squared and Visualization Analysis**

<p align="center">
  <img src = ./Images/EDA2>
</p> 
Here is the break down of the chi-squared results, considering that the null hypothesis in each instance is that each feature has no relationship with readmission and the alpha value is 0.05:

1. All of the medication related categories seem to have a significant relationship with readmission
2. Discharge disposition has the strongest relationship with readmission, suggesting that it will be an important feature for modeling.
### **Numerical Feature Pearson's Correlation Analysis**

<p align="center">
  <img src = ./Images/EDA>
</p> 

None of the numerical features appear to have significant linear relationship with easly readmittance. Knowing this helps narrow down which type of models to consider.

### **Principal Component Analysis**

After preprocessing the data, which included one-hot encoding, the  dataframe again has 50 features. A PCA was conducted to attempt to reduce dimensionality and noise.

<p align="center">
  <img src = ./Images/PCA1.png>
</p> 

<p align="center">
  <img src = ./Images/PCA2.png>
</p> 

According the the visuals, 12-14 features seems to be the optimal amount of components to use.

## Modeling

### **Logistic Regression**

<p align="center">
  <img src = ./Images/logisticCM.png>
</p> 

#### **Logistic Regression Summary**

Initially, I intended to use recall as my primary metric. However, this approach consistently led to my models predicting all instances as class 1, or readmitted. While this strategy technically minimizes false negatives (patients who are readmitted but not identified as at risk), it doesn't offer practical benefits. To address this issue, I've decided to prioritize precision. This metric helps balance out the number of false positives and provides a more practical evaluation of model performance.

Similar to the models with three categories for readmission, this binary classification model also struggles to effectively categorize the target class of interest. While the model performs reasonably well overall, it falls short of meeting the specific business requirements for accurately predicting early readmissions.

### **XGBoost**

#### **XGBoost Summary**
XGBoost's final model did much better at categorizing the focus class than logistic regression

However, recall for class 1 is 0.55, indicating that the model captures 55% of all actual instances of class 1 in the dataset. While this suggests a relatively higher sensitivity compared to precision, it still indicates that the model misses a considerable portion of class 1 instances.

### **Random Forest**

<p align="center">
  <img src = ./Images/RandomForest1.png>
</p> 

<p align="center">
  <img src = ./Images/RandomForest2.png>
</p> 

#### **Random Forest Summary**

Hyperparametric Tuning the Random Forest did result in a model that did better than XG Boost, but marginally. And according to my metric, precision it did worse.

Feature importance did not seem to improve the model in a significant way.

## Results
#### 1. Modeling and Limitations
While this notebook doesn't encompass exhaustive evidence of every model and fine-tuning attempt I made, it does showcase two primary approaches I explored. Given more time, I would have also liked to include examples of oversampling techniques.

I'd also like to try more ensembling and stacking methods.

Overall, the models achieved an accuracy of around 60%, with particularly poor performance in identifying the target class. Upon comparing my work with the efforts of others, I am inclined to believe that this dataset may not be inherently conducive to accurate predictive modeling for this specific task.

Ideally, I would seek input from individuals with more experience and expertise to assess the suitability of this dataset for predictive modeling purposes.

#### 2. Project Gains

While I didn't achieve the initial objectives I set out for, this project provided valuable learning opportunities.

On a personal level, I gained insights into various challenges and strategies associated with handling an imbalanced target variable.

Furthermore, the features identified as significant can serve as valuable starting points for further research into readmission risk factors.

## Repository Structure
├── Data
├── Images
├── .gitignore
├── Diabetic_Discharge_Navigating_Readmission_Risks.ipynb.gitignore
├── Diabetic_Discharge_Navigating_Readmission_Risks.pdf
├── README.md
