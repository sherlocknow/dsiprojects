# Project 2 - Ames Housing Data and Kaggle Challenge - Vikas Kalia

## Problem Statement
Iowa's Amex Assessor's office has a very comprehensive set of data on the sales transactions of the houses across some of its neighborhoods. Given the rich quality of the data, there is an opportunity to use data science modeling techniques to predict sale price for any new property that comes up for sale in these neighborhoods. Challenge of this project is to conduct a detailed EDA & feature engineering with very high number of features available with the datasets.

### Executive Summary
Objective of this project is to use past housing dataset with sale price and apply linear regression modeling after data cleaning, preprocessing, feature engineering and exploratory data analysis. Through model evaluation process, regularization techniques like Ridge and Lasso will be leveraged to tune the model to predict sale price of the house provided in the test dataset. Finally, summary of the analysis of modeling process will be documented and predicted sale price for houses in the test dataset will be submitted to Kaggle to get root mean square error of the predicted sale prices.

### Contents table below provides the framework used to conduct this study & submission*.
- **Import Data Science Libraries**
- **Load Data**
- **Phase 1 Data Cleaning, EDA & Feature Engineering**
- **Phase 1 Modeling - Training & Evaluation**
- **Phase 1 Submission of predictions to Kaggle**
- **Phase 2 EDA & Feature Engineering**
- **Phase 2 Modeling - Training & Evaluation**
- **Phase 2 Submission of predictions to Kaggle**

### Project Summary Report is provided at the bottom of this report.

'*Note: While listed in sequence, these activities listed above are iterative in nature, so the flow can be back and forth among these activities to ultimately to select the best features as predictors of the target variable, i.e. sale price.'*

### Jupyter Notebooks list:
**Following notebooks are created to complete this study**
- **/code/Main_Project_2_VK.ipynb** - Main notebook
- **/code/Train_test_split_Project_2_VK.ipynb** - for train_test_split the train dataset
- **/code/Phase 1 Modeling_Project_2_VK.ipynb** - for phase 1 - modeling, submission of prediction to Kaggle.
- **/code/Phase 2 Modeling_Project_2_VK.ipynb** - for phase 2 - modeling, submission of prediction to Kaggle.


### Datasets
**Datasets used - downloaded from Kaggle:**
- '../datasets/test.csv'
- '../datasets/train.csv'
- '../sample

**Datasets created**
***Through inital train_test_split of train dataset***
- '../datasets/x_train.csv'
- '../datasets/x_test.csv'
- '../datasets/y_train.csv'
- '../datasets/y_test.csv'

**Post data cleaning, EDA, preprocessing and feature engineering**

For **Phase 1** of feature selection and modeling
- '../datasets/x_train_for_mod.csv'
- '../datasets/x_test_for_mod.csv'
- '../datasets/y_train_for_mod.csv'
- '../datasets/y_test_for_mod.csv'
- '../datasets/test_for_mod.csv'

For **Phase 2** of feature selection and modeling
- '../datasets/x_train_for_mod_p2.csv'
- '../datasets/x_test_for_mod_p2.csv'
- '../datasets/y_train_for_mod_p2.csv'
- '../datasets/y_test_for_mod_p2.csv'
- '../datasets/test_for_mod_p2.csv'

**Datasets submitted**
- '../datasets/submission.csv'       <== 'Intial submission with just one predictor'
- '../datasets/submission_lassoCV.csv' <== 'Submission with predictions from phase 1 lassoCV model'
- '../datasets/submission_lassoCV_p2.csv' <== 'Phase 2 submission with predictions from lassoCV model'
- '../datasets/submission_lr_p2.csv' <== 'Phase 2 submission with predictions from lr model'

### DataFrame naming convention for Main Notebook**
- Training DataFrame name : df
- Training Target(y) DF name : y_train
- Validation DataFrame name : df_test
- Validation Target(y) DF name : y_test
- Test DataFrame name: test

### Threshholds used for data cleaning and preprocessing**
- For categorical features with two only classes, if one of the class is in more that 95% of the observations, then that feature will be dropped from the modelling
- For categorical features with more than two classes, if one of the class is in more that 70% of the observations, then that feature will be dropped from the modelling
- Any feature with more than 30% of observations with missing values will be dropped
- Among numerical features, inital plan is drop all features within +.4 and -.2 values of corr coef with target variable SalePrice. Only exception is 'Lot Area' feature with corr lower than .4. and will explained below
- If the correlation among the two predictors is greater than .8, then the feature with lower correlation with SalePrice will be dropped

### Approach for Dropping Features
- All numercial features are dropped in one place and all categorical features are dropped in one place in the notebook for better tracability, even though the discovery and decision to drop those are made at different stages. Only exception is for the columns that are dropped after the one-hot-encoding to match columns among train and test DFs.
- Selected features are always dropped from three dataframes i.e. df, df_test & test.

### Approach for Dropping Observations(rows)**
- Selected observations are always dropped from two dataframes i.e. df, y_train.

## Project Summary Report
### Phase 1  - Data Cleaning, EDA & Feature Engineering
**Observations & Actions:**
- Train dataset has 2051 observations and 81 features
- Test dataset has 879 observation and 80 features, without the target variable of SalePrice.
- One time train_test_split was done on the Train dataset with .25 ratio and those datasets were used for rest of the activities in the project.
- A logical separation of new train dataset (df) was done to analyse numerical and categorical features separately.
- First, analysed for null values in numeric features and various imputation techniques were leveraged to replace null values.
- Some features were dropped as per the threshhold described in the 'Executive Summary'.
- Outliers for SalePrice in the train was analysed and observation above $500,000 of SalePrice were dopped to shorten the tail of the distribution curve.
- Three new features were added to replace 1) the year when house was built, 2) was last remodeled, and 3) the year when garage was buit
- Second, analyzed for categorical values, conducted visual data analysis to see how the IQRs of classes within each categorical feature mapped to SalePrice by using boxplots. Features with IQRs of their classes overalapping against SalePrice are dropped. And features with IQRs not overallping against SalePrice are checked for value count and if one of the class dominates, then that feature is dropped.
- Selected categotical features were then clead, nominal feature are hot encoded and ordinal features are given numerical order.
- Number of features selected were 17 numerical and 10 categorical features made of 2 nominal and 8 ordinal features coverting to 35 features, totaling it all to 52 predictors for phase 1 of modeling.

### Phase 1 - Modeling

- Created first submission file for Kaggle by using linear regression with just one predictor i.e. 'Overall Qual'.
- During the phase 1 of modelling, built baseline model, linear regression model, LassoCV and ElasticNetCV model listed below are the RMSE score from each of the model.  

**Baseline Model:**
- R2 score for the baseline model on validation dataset:  -0.0006156545387887569
- MSE score for the baseline model on validation dataset::  4858364177.975382
- **RMSE score for the baseline model on validation dataset: 69701.9668156888**

**Regression Model:**
- R2 of LR model on X_train:  0.8682261301880155
- R2 of LR model on X_test:  0.8154686074094704
- MSE of LR on X_train data: 750682679.5139594
- MSE of LR on X_test  data: 895969100.0306927
- **RMSE of LR on X_testdata: 29932.742941980654**

<u>Findings from LR Model</u>
- LR model has performed better than the baseline model
- LR model was marginally overfitting as per R2 and MSE scores.
- Residual analysis was conducted on the lr model prediction and two of the LINE assumptions were evaluated. Although it can't be concluded with certainity however, distribution Curve of residuals being very close to normal, scatter plot along with actual values being very close to linear shape and scatter plot with predicted values being symetrical roughly indicates that model is quite well balanced and will generalize quite well

**RidgeCV Model with CV=5 and alpha range of logspace(0.1, 10, 100)**
- Optimal alpha value suggested by ridgeCV with cv=5: 398.1071705534973
- R2 score from ridgeCV model with CV=5 on X_train_scaled: 0.8629281222657397
- R2 score from ridgeCV model with CV=5 on X_test_scaled: 0.8160483447876532-
- MSE from ridgeCV on X_train_scaled: 780864101.5884181
- MSE from ridgeCV on X_test_scaled: 893154257.6903589
- **RMSE from ridgeCV on X_test_scaled: 29885.68650190855**

<u>Findings from RidgeCV Model</u>
- RidgeCV RMSE score are marginally better than the LR RMSE scores.

**LassoCV Model with number of alphas as 100**
- Optimal alpha value suggested by lassoCV with cv=5: 762.4727401079197
- R2 score from lassoCV model with CV=5 on X_train_scaled:0.8649475393461086
- R2 score from lassoCV model with CV=5 on X_test_scaled:0.8183342390822687
- MSE from lassoCV on X_train_scaled: 769359989.0727081
- MSE from lassoCV on X_test_scaled:882055383.8068427
- RMSE from lassoCV on X_test_scaled:29699.41723008791

<u>Findings from LassoCV Model</u>
- RMSE score for LassoCV was marginally better than RidgeCV and LR models.
- Out of 52, 17 features were allocated zero coefficient value.
- While 'Garage Area' had higher corr coef with SalePrice, however 'Lot Area' has higher lassCv coef than 'Garage Area'. That could be explained due to high collinearity between 'Garage Area' and 'Garage Cars'.

**ElasticNetCV Model with 50:50 ratio**
- Optimal alpha value suggested by ElasticNetCV With cv=5: 123.69302942764524
- R2 score from ElasticNet CV model with CV=5 on X_train_scaled: 0.20985665080001803
- R2 score from ElasticNet CV model with CV=5 on X_test_scaled: 0.21097576240143778
- MSE from ElasticNetCV on X_train_scaled: 4501248444.960153
- MSE from ElasticNetCV on X_test_scaled: 3831008513.723579
- **RMSE from ElasticNetCV on X_test_scaled: 61895.141277192175**

**ElasticNetCV Model with 90:10 ratio**
- Optimal alpha value suggested by ElasticNetCV With cv=5: 68.7183496820251
- R2 score from ElasticNet CV model with CV=5 on X_train_scaled: 0.6842997507819564
- R2 score from ElasticNet CV model with CV=5 on X_test_scaled: 0.6735451454688607
- MSE from ElasticNetCV on X_train_scaled: 1798465123.2020822
- MSE from ElasticNetCV on X_test_scaled: 1585060721.153018
- **RMSE from ElasticNetCV on X_test_scaled: 39812.82106499134**

<u>Findings from ElasticNet Model</u>
- While there was a significant improvement when the ratio between LassoCV and RidgeCV where changed from 50:50 to 90:10, however it still did not perform better than LassoCV model.

### Phase 2 -  EDA & Feature Engineering
**Observations & Actions:**
- Features with **zero** coefficient value from LassoCV model were dropped.
- Collinearity among the remainng features was analyzed and few three more columns dropped
- Further reduction in the SalePrice outliers observation was done.

### Phase 2 Modeling
There were multiple iteration of features selection and adjustment in level of outliers reduction and as documented in phase 2 modeling notebook as well, the RMSE score for phase 2 - Lr and LassoCV models were better than phase 1 - LR and LassoCV score. If more time was available,more could have been explored about interaction terms among the features and its impact on the performance of the models.

The best combination of feature and SalePrice outlier was used for the final selection among the submisions on Kaggle i.e **submission_lr_p2.csv**.

## Conclusion:
**For the training data that was provided for this competition, the Linear Regression model that is well balanced and generalizes well could be built through combination of conducting detailed feature selection through EDA, feature Engineering, and regularization by LassoCV model.**
