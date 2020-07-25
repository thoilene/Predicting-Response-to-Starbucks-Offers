# Starbucks-Capstone-Challenge

- This is the final project in the context of the Nanodegree program "Data Science"
- It intends to show the ability of the student to apply data science methodology and machine learning techniques in business real life.

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

- Could the response of a given user to a given offer be precited ? Will a given user respond to a given offer ?
- What are the most importants factors when it is about to predict the responsiveness of a user to an offer ?

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

The results of this project are presented in the section "Conclusion" of the Jupyter notebook Starbucks_Capstone_notebook.ipynb. The conclusion is a summary of the answers to the business questions asked above. 
The main technical challenge of this project is the logical combination of transactional data. As offers have been received 66501 times, this is the amount of records which have to be combined to all other data. The runtime of the corresponding routine is relatively long. 

The predictive model built in this project for predicting the response of a user to an offer demonstrates a performance of 81.41% accuracy on training data and 71.80% accuracy on test data.

However, the performance results achieved in this project could be improved using different machine learning techniques like parameter tuning or the use of other classification models.
