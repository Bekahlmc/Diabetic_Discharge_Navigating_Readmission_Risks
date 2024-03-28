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
  <img src = ./Images/Screenshot 2024-03-28 at 7.22.43 AM.png>
</p> 

<p align="center">
  <img src = ./Images/Screenshot 2024-03-28 at 7.24.00 AM.png>
</p> 

<p align="center">
  <img src = ./Images/Screenshot 2024-03-27 at 6.50.36 PM.png>
</p> 

### **Categorical Feature Chi-Squared and Visualization Analysis**

Here is the break down of the chi-squared results, considering that the null hypothesis in each instance is that each feature has no relationship with readmission and the alpha value is 0.05:

1. All of the medication related categories seem to have a significant relationship with readmission, as well as admission type and primary diagnosis.

2. Discharge disposition has the strongest relationship with readmission, suggesting that it will be an important feature for modeling.

3. Gender and admission source's chi-squared results do not demonstrate a strong relationship with the target.

### **Numerical Feature Pearson's Correlation Analysis**

<p align="center">
  <img src = ./Images/Screenshot 2024-03-28 at 7.22.43 AM.png>
</p> 

None of the numerical features appear to have significant linear relationship with easly readmittance. Knowing this helps narrow down which type of models to consider.

### **Principal Component Analysis**

After preprocessing the data, which included one-hot encoding, the  dataframe again has 50 features. A PCA was conducted to attempt to reduce dimensionality and noise.

<p align="center">
  <img src = ./Images/Screenshot 2024-03-27 at 6.48.36 PM.png>
</p> 

<p align="center">
  <img src = ./Images/SScreenshot 2024-03-27 at 7.06.49 PM.png>
</p> 

According the the visuals, 12-14 features seems to be the optimal amount of components to use.
