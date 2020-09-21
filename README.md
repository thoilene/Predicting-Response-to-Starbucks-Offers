# Predicting Response to Starbucks offers - Using Machine Learning

### Introduction

This data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). Some users might not receive any offer during certain weeks.

The Starbucks rewards app allows users to earn rewards when they pay through that app. The process of earning rewards consists of receiving, displaying and completing offers. One important issue concerns the responsiveness of app users who receive offers:

- Could the response of a given user to a given offer be precited ? Will a given user respond to a given offer ?
- What are the most importants factors when it is about to predict the responsiveness of a user to an offer ?

Other questions concerning the business could be adressed in this context as they are closely related to the responsiveness of app users: 

- Which are the most accepted offers ?
- Which are the most beneficial offers from the perspective of revenues ?
- What is the profile of the typical/ideal target user (age, income, gender) ?

The answers to these questions could help the company in various ways. By avoiding sending offers to users who are less likely to respond, the company could save advertising costs. This would also allow the company to work more efficiently by targeting those people who are more likely to respond to certain offers. The section "Exploratory Data Analysis" below gives deep insights into the data. The conclusion at the end of this Jupyter notebook provides a summary of the answers to all questions asked here.

# Requirements
The following libraries have been used for this project under Anaconda distribution:

- Python 3.7.4
- numpy 1.16.5
- pandas 0.25.1
- seaborn 0.9.0
- matplotlib 3.1.1
- sklearn 0.21.3

# Project motivation

The Starbucks rewards app allows users to earn rewards when they pay through that app. The process of earning rewards consists of receiving, displaying and completing offers. One important issue concerns the responsiveness of app users who receive offers:

- Could the response of a given user to a given offer be predicted ? Will a given user respond to a given offer ?
- What are the most important factors when it is about to predict the responsiveness of a user to an offer ?

Other questions concerning the business could be adressed in this context as they are closely related to the responsiveness of app users:

- Which are the most accepted offers ?
- Which are the most beneficial offers from the perspective of revenues ?
- What is the profile of the typical/ideal target user (age, income, gender) ?

The answers to these questions could help the company in various ways. By avoiding sending offers to users who are less likely to respond, the company could save advertising costs. This would also allow the company to work more efficiently by targeting those people who are more likely to respond to certain offers. 

# Files in the Repository

This repository contains basically a Jupyter notebook and a subfolder for data:
- Starbucks_Capstone_notebook.ipynb: Jupyter notebook containing the code and all steps of the project including business understanding, data understanding, data preparation, model building, model evaluation and conclusion.
- /data (subfolder for data files):
  - portfolio.json: offer data (offer type, rewards, duration, etc...)
  - profile.json: user data (age, income, gender)
  - transcript.zip: contains transactional data in .json-format

# Results

The results of this project are presented in the section "Conclusion" of the Jupyter notebook Starbucks_Capstone_notebook.ipynb. The conclusion is a summary of the answers to the business questions asked above at the beginning of the project. 
The main technical challenge of this project is the logical combination of transactional data. As offers have been received 66501 times, this is the amount of records which have to be combined to all other data. The runtime of the corresponding routine is relatively long. 

The predictive model built in this project for predicting the response of a user to an offer demonstrates a performance of 81.41% accuracy on training data and 71.80% accuracy on test data.

However, the performance results achieved in this project could be improved using different machine learning techniques like parameter tuning or the use of other classification models.

## Conclusion

The central problem I have chosen to solve in this Starbucks Capstone Challenge is predicting the responsiveness of a user to a given offer sent through Starbuck reward app.


### Data preparation and analysis

The data preparation step had been focused on removing missing values, splitting complex data into columns and combining transcript data in a logical way which allows to assess successful user response.

2175 profiles with wrong age, missing income and gender have been detected and removed. Transcript data have been combined to get successful responses only for those records received, viewed, completed or paid within the duration of the offer. The combination of the data here is the major challenge in the data preparation phase. 66501 entries have to be processed one by one, taking around 50 minutes runtime as python multiprocessing technique is not used in Jupyter notebook. The same could be achieved within 10 minutes with multiprocessing technique on regular python script.

After merging combined transactional data to profile and portfolio data, an exploratory analysis has made some insights visible.  Hence, the questions asked in section 1. could be answered.

### Results and answers to initial questions

**- Which are the most accepted offers ?**

The following 3 offers have been mostly responded by users.They are the most accepted offers so far:

    - fafdcd668e3743c1bb461111dcafc2a4
    - 2298d6c36e964ae4a3e7e9706d1fb8c2
    - f19421c1d4aa40978ebb69ca19b0e20d

**- Which are the most beneficial offers from the perspective of revenues ?**

The following two offers have generated the highest revenue

    - fafdcd668e3743c1bb461111dcafc2a4
    - 2298d6c36e964ae4a3e7e9706d1fb8c2
    
The 2 most successful offers are of type "discount", have a duration of 7 or 10 days and reward of 2 or 3.
    
**- What is the profile of the typical/ideal target user (age, income, gender) ?**

The typical/ideal target user are basically those who respond to offers and allow for generating revenue. As seen in exploratory analysis, users aged between 40 and 70 years having an income between 50000 and 100000 are those who respond the most to different offers and generate the highest revenues. Women respond proportionally more than men and generated more revenue than men. It would make sens to invest in getting more women as member.

**- Could the response of a given user to a given offer be predicted ? Will a given user respond to a given offer ?**

The predictive model build in this project is a classifier based on random forest logics. The best cross-validated model which is the one with the best average performance shows 81.41% accuracy on training data and 70.80% accuracy on test data. The f1-scores of 80.70% on training data and 69.45% on test data are at the same range as accuracy scores above. Hence, it could be predicted with at least 70.80% accuracy whether a user will respond to an offer or not. 

***Interpretation:*** *81% accuracy of the model means that if the model is used to predict the reaction of the users in 100 cases to some offers, it will tell the truth in 81 cases. In comparison to that, the naive predictor defined above would tell the truth only in 49 cases out of 100.*


**- What are the most important factors when it is about to predict the responsiveness of a user to an offer ?**

The age and income of the users are the most important factors explaining the responsiveness of the users to different offers. However, the year/month where the user became a member expressing the loyalty are also important role in this context. The use of social media also one of the 5 most important factors according to the model.

### Predictive model

The random forest classifier of the sklearn library (with decision tree classifier as base estimator) has been chosen as predictive model in this project. The information gain technique of decision tree classifier combined with random forest technique was expected to be the most appropriate model as some features (like age, income, offer type) are particularily impacting the outcome of the prediction. 
The random search cross-validation has been applied to choose the best random forest classifier. The cross-validated model as result of the random serch is more stable and slightly less overfitted than than the original model. The performance results of the model are summarized above in this section.


### Future model improvement

However, the performance results achieved here could be improved using different machine learning techniques like parameter tuning or the use of other classification models. 

The use of neural networks or some other classifiers could help improving the performance. Deep learning techniques could also be investigated in this context. 
Another improvement will follow by applying the recursive feature elimination (RFE). This will allow to eliminate those features which do not really improve the performance of the model.


### References

A blog post on this project is published here:
https://thomasilene.wixsite.com/website/post/starbuck-s-rewards-app-predicting-user-s-reaction-to-some-offers

