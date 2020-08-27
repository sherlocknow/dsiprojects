# Project 2 - Ames Housing Data and Kaggle Challenge - Vikas Kalia

### Problem Statement
City of Boston has very comprehensive set of data on the sales transactions of the houses across some of its neighbourhoods. Given the rich quality of the data, there is an opportunity to use data science modeling techniques to predict sale price for any new property that comes up for sale in these neighbourhoods.
### Executive Summary
Objective of this project is to use past housing dataset with sale price and apply linear regression modeling after data cleaning, preprocessing, feature engineering and exploratory data analysis. Through model evaluation process, regularization techniques like Ridge and Lasso will be leveraged to tune the model to predict sale price of the house provided in the test dataset. Finally, summary of the analysis of modeling process will be documented and predicted sale price for houses in the test dataset will be submitted to Kaggle to get root mean square error of the predicted sale prices.

**Contents table below provides the framework used to conduct this study & submission**.
- Import Data Science Libraries
- Load Data
- EDA and Data Cleaning
- Preprocessing & Feature Engineering
- Modeling - Training & Evaluation
- Submission of predictions to Kaggle
- Project Summary Report

'*Note: While listed in sequence, these activities listed above are iterative in nature, so the flow can be back and forth among these activities to ultimately to select the best features as predictors of the target variable, i.e. sale price.'*

### Jupyter Notebooks list:

Following notebooks are created to complete this study
- '../code/Main_Project_2_VK.ipynb' - Main notebook
- '..'/code/Train_test_split_Project_2_VK.ipynb' - Notebook to train_test_split the train dataset
- '../code/Modeling_Project_2_VK.ipynb' - Notebook for modeling, submission of prediction to Kaggle and Project Summary Report.

### Datasets
**Datasets used - downloaded from Kaggle:**
'../datasets/test.csv'
'../datasets/train.csv'
'../sample

**Datasets created Through inital train_test_split of train dataset**
'../datasets/x_train.csv'
'../datasets/x_test.csv'
'../datasets/y_train.csv'
'../datasets/y_test.csv'

**Post data cleaning, EDA, preprocessing and feature engineering**
'../datasets/x_train_for_mod.csv'
'../datasets/x_test_for_mod.csv'
'../datasets/y_train_for_mod.csv'
'../datasets/y_test_for_mod.csv'
'../datasets/test_for_mod.csv'

**Datasets submitted**
'../datasets/submission.csv' <== 'Intial submission with just one predictor'
'../datasets/submission_lasso.csv' <== 'Final submission with predictions from lassoCV model'

**DataFrame naming convention for Main Notebook**
- Training DataFrame name : df
- Training Target(y) DF name : y_train
- Validation DataFrame name : df_test
- Validation Target(y) DF name : y_test
- Test DataFrame name: test

**Threshholds used for data cleaning and preprocessing**
- For categorical features with two only classes, if one of the class is in more that 95% of the observations, then that feature will be dropped from the modelling
- For categorical features with more than two classes, if one of the class is in more that 70% of the observations, then that feature will be dropped from the modelling
- Any feature with more than 30% of observations with missing values will be dropped
- Among numerical features, inital plan is drop all features within +.4 and -.2 values of corr coef with target variable SalePrice. Only exception is 'Lot Area' feature with corr lower than .4. and will explained below
- Approach for Dropping Features
- All numercial features are dropped in one place and all categorical features are dropped in one place in the notebook for better tracability, even though the discovery and decision to drop those are made at different stages. Only exception is for the columns that are dropped after the one-hot-encoding to match columns among train and test DFs.
- Selected features are always dropped from three dataframes i.e. df, df_test & test.

**Approach for Dropping Observations(rows)**
- Selected observations are always dropped from two dataframes i.e. df, y_train.

## Project Summary Report
