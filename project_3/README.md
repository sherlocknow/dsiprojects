## Project 3: Web APIs & Classification - Vikas Kalia

## Problem Statement
I work in the credit card industry and my marketing and legal team would like to review social media posts like Reddit site for current discussion on credit cards. However, many times the posts under r/CRedit subreddit are actually relevant to Credit Card business.
So there is an opportunity to build a predictive model which is able to classify any new reddit posts in r/CreditCards and r/CRedit subreddits, that should belong to Credit Cards for marketing and legal teams to review.

## Executive Summary
Data science framework is leveraged to scrape the posts from two subriddits of reddit.com. Data is then cleaned, and transformed for exploratory data analysis. Word vectorizers are leveraged to engineer pots into word vectors. NPL classifier Naive Bayes as well as Logistic regression are used to build model on word vectors. Evaluation techniques like confusion matrix, K-fold cross validation, coefficient analysis, probability distribution and roc_auc curve are leveraged. Finally, accuracy and roc_auv scores are used as metric to determine the model which is best suited to classify Credit Card posts.


### Contents table below provides the framework used to build this predictive model.
- **Import Data Science Libraries**
- **Download posts from r/CreditCards and r/CRedit**
- **Conduct EDA and data cleaning and feature engineering**
- **Modeling - Training & Evaluation**
- **Conclusions and Recommendations**

### APIs
Credit Cards Posts : https://www.reddit.com/r/CreditCards.json
Credit Score Posts : https://www.reddit.com/r/CRedit.json

### Jupyter Notebooks list:
**Following notebook are created to complete this study**
- **/code/Project_3_VK.ipynb** - Main notebook


### DataSets
../data/posts_cc_1.csv  => initial list of downloaded posts for r/CRedit subreddit
../data/posts_cr_1.csv  => initial list of downloaded posts for r/CreditCards subreddit
../data/post_cc.csv.    => saved for futher ongoing reference for EDA, Data Transformation and Modeling.
../data/post_cr.csv.    => saved for futher ongoing reference for EDA, Data Transformation and Modelin
../data/comb_cc_cr.csv  => saved combined list of subreddits

### Modeling Approach
As per the problem statement we are only trying to correctly classify the subreddit correctly. so the only measure used to evaluate the models will be accuracy of classificaiton. Two modeling techniques i.e. Naive Bayes and Logistic Regression are applied on features vectors created by CountVectorizer as well as TF-IDF word vectorizer.
Each model will evaluated with cross_validation method, confusion matrix and Logistic Regression models will be tuned using GridSearchCV method.
**Note:** CreditCards is designated positive class and CRedit is designated negative class

###  Conclusions

**After evaluating and tuning Naive Bayes and Logistic Regression model and using accuracy and roc_auc scores, it is concluded that model built with Logistic regression and Tf-IDF Word vectorizer will be used for future selection of subreddits r/CreditCards & r/Credit from reddit to have one list of posts which is relavent to Credit Card business, for marketing and legal teams to review.**

### Recommendations
- **More analysis can be done to identify common words across the subreddits**
- **Techniques like pipeline & GridSearch could be leveraged for estimating hyper-parameters for word vectorizers.**
- **As first version of the nlp classification model is ready, team could evaluate posts related to Credit Cards on other social media sites with this classifier.**
