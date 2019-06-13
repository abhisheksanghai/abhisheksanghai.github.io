---
layout: post
comments: true
title: "Journey of Data Science Project"
date: 2019-06-13
---

As we start working on an Analytics Project, we tend to think about the algorithms we are going to use and hence, as a data scientist our focus never really shifts to the other very important attributes. Although knowledge about various algorithms available is going to be very useful in coming up with the solutions but the process of model building involves much more than just agorithms. We need to have data in the usable format and with correct set of features for the model to give useful results. Without proper business knowledge infused into the data preparation, the results out a model is most probably going to be just garbage. In fact, the data preprocessing takes up most of the time in a model building exercise. So, let's list down the steps to be followed while executing a Machine Learning Project -

### 1. Defining Objective

The first step of any model building process has to be defining the objective. This will involve understanding how a business functions (domain knowledge is very crucial) and how it will use the data. It's very critical to be on the same page with your stakeholders in terms of what is expected at the end of the project. It's also important to get an understanding of how the results will be used for implementation as it might affect the approach taken during the exercise. Also, various departments within an organization might consume the results in a very different manner. Someone working on the field might want a very granular level insights while on the other hand someone like a CEO might just want info about Key Performance Indicators(KPIs). Overall, this step includes mapping out business objectives.

### 2. Transforming Business Objectives to Data Goals

Now that we have a clear understanding of what the business requirements are, we have to think about the data required for project execution. This step is often missed by the practitioners or is considered once the data is available from the clients end. This will lead to lost opportunity of giving valuable suggestions to your client for tracking additional data as once we have seen the data, it becomes difficult to think about all the possible factors from an open mind. For this, we should interview the subject matter experts from the client's side as well as from our own organization. They will help us create hypothesis based on their domain knowledge. We will then use these hypothesis to come up with the set of data required. The list of hypothesis collated is also going to be helpful in the data exploration stage as we will have a direction to move into as we try to test them for their validity.

### 3. Data Gathering

Next, we start gathering data from various sources. This might require the help of a data engineer depending on the scale and complexity of the data. First, we need to identify all the sources from which we will obtain the data. Different data sources might be -
- Clients giving access to their database.
- Clients transferring data through flat files.
- External Sources - This might involve scrapping data from various websites.

Some social media platforms provide their own APIs (Application Program Interface) for accessing data. But the introduction of GDPR(General Data Protection Regulation) means one cannot access a user's data without their consent. Appropriate changes have been made in the APIs accordingly.

### 4. Data Preprocessing / Exploratory Analysis

Once we have all the data from the required sources available to us at a single location, we transform it into usable form. Most of the times, raw data won't be available in a format that can directly be used to generate insights and hence, their transformation is a necessary step. Next, we start exploring data for possible insights. Exploratory analysis can be split into three levels - Univariate Analysis, Bivariate Analysis and Multivariate Analysis. Univariate analysis involves looking for missing values and identifying the distribution of each variable independently. Missing values and outlier values are treated as per the requirement and business logic involved. In bivariate and multivariate analysis we try to look for relationship between two or more variables that might help us come up with certain variable transformations required (Most of the times we are looking for ways to create linear relationships). These steps also help us explore various features that might be created in order to solve the problem at hand. While this entire exercise goes on, we also have to test the hypothesis we designed earlier and verify them for their validity.

### 5. Model Selection and Validation

Post Exploratory Analysis comes the time for using some algorithms. For this, we have to first split the data into 2 sets i.e. Train and Test. Train data (usually 70-80% of total) is used for developing the model while test data (ususally 20-30% of total) is used for verifying if the model holds good on unseen data. More often cross validation is considered a better way of testing this where we create multiple sets of train and test data and look for consistency in the results. This helps us in understanding the robustness and reliability of the model. In case the model does not yields desired results, we might try different algorithms or look for feature engineering and create new variables in order to improve model performance. Ensemble Methods are also a great way of improving model performance.

### 6. Model Deployment and Maintenance

Now that we have our model tested and ready to be in action, we need to deploy it. By deployment, we mean transferring the analytical results into effective decision making. This might be done through Business Intelligence Reports or we might need to integrate the model with clients decision making applications. Post this, we observe the model results on field testing and referesh the model at regular time intervals if required. We might also need to rebuild the model after certain time period if the model results deteriorates beyond acceptable limits.
