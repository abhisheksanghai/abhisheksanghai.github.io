---
layout: post
comments: true
title: "Algorithms in Machine Learning"
date: 2019-05-23
---

Model refers to a rule, equation or a structure that helps a machine take decisions. Machine Learning (ML) models are in general, a tool useful to establish relationships or find patterns in the data. But as all the good things come with caution, so does Machine Learning. As it is wisely said, all models are wrong, only some are useful. The results from the models should always be verified to make sense from the business perspective.
ML is majorly divided into two types namely, **supervised and unsupervised learning**. **Reinforcement Learning** has emerged as the new section in recent times.

## Supervised Learning

In supervised learning, we have the outcome defined in the form of a variable and the objective is to reach as close as possible to this outcome variable (dependent variable). For this purpose, we use a lot of external information that might help us determine what the value of this outcome variable could be. We call these external factors as predictors or independent variables. These models are of two types i.e. **Regression and Classification**. For achieving our objective, we define an error metric (that tells us the difference between actual and predicted values) and try to minimize it.

Regression Models have continuous variable as outcome while classification Models are defined for categorical outcome variables.

### Regression Models

1. [Linear Regression](https://abhisheksanghai.com/2019/06/18/linear-regression) - It is the most prominent of the Regression models and forms the foundation of machine learning. These models 
are in the form of a linear equation,  y = &theta;x + c, where y is the dependent variable, x is the independent variable. Once this equation is obtained by minimizing an error metric, we try and use it for prediction.

2. Polynomial Regression - This is an alternate form of Linear Regression where the independent variables have degrees associated with  them. Think of it as having multiple variables such as x, x<sup>2</sup> etc.

3. CART (Classification and Regression Trees) - This is a decision tree form of model which takes rule based approach for reaching the objective.

A lot of times, the predictions turn out pretty accurate for the data model was built on, but it fails to give good results for out of sample data. This phenomena is called **overfitting**. This happens because the model alongwith learning the required pattern in the data, learns the noise in the data as well. So, if the out of sample data does not have the noisy pattern, it's prediction will be bad.

One way to deal with this is **regularization**. Regularization allows us to add a penalty parameter to the error metric that slightly alters our objective function and doesn't allow us to reach the true minimum and in turn prevents the model from learning noise in the data. Following are different types of regularization commonly used for Linear Regression - 

- Lasso Regression or L1 Regularization
- Ridge Regression or L2 Regularization
- Elastic Net Regression

### Classification Models

1. [Logistic Regression](https://abhisheksanghai.com/2019/09/07/logistic-regression) - It is a classification technique which gives out probability of an event occuring based on a transformed linear equation. The probability is then used for taking the decision.

2. Decision Tree - These are tree based approaches that gives out a set of rules to determine the output. There are multiple algorithms 
used for decision tree.

3. SVM (Support Vector Machine) - SVM unlike most of the algorithms tries to classify outcome non linearly. It transforms data into a higher dimension and then use it for classification. In lower dimension it appears that the separation plane is non linear. This is achieved through the use of kernels.

4. Naive Bayes - These are probability based classifiers that works on extended bayes theorem.

5. K-NN Classification - In these models, we look for outcome of k nearest neighbouring data points in order to make a decision.

Let's move onto Unsupervised Learning now.

## Unsupervised Learning

These models do not have any outcome variables defined,rather, they are majorly used for segmenting data into unknown groups with similar characteristics. All the **Clustering Models** fall under this category. **Association Rules** and **Dimensionality Reduction** are also considered as Unsupervised Learning.

### Clustering

Clustering refers to dividing a population into multiple groups such that the the data points in the same group are more similar to each other than to data points from other groups.

1. K-Means Clustering - These models work with euclidian distance between data points to form clusters and are the most preferred method for clustering. 

2. Agglomerative Hierarchical Clustering - In this technique, we first consider all the data points as individual clusters and then keep combining them one by one based on similarity. The output is represented through a tree like diagram called Dendogram. 

### Association Rules

1. Apriori Algorithm - This is a probabilty based algorithm and is primarily used for Market Basket Analysis where we look for products often bought together and then form product bundles.

### Dimensionality Reduction

Often in model building exercise, we find ourselves dealing with far more no. of variables than we can use in the model. It leads to a situation where we either drop variables or combine them together to come up with a new variable. The techniques involving combination of variables comes under this section.

1. Principal Component Analysis (PCA) - This technique combines n variables and gives out new variables with the objective of maximising the variance in the data so that the loss of information is minimal. PCA can be used for feature extraction as well.

2. Singular Value Decomposition (SVD) - This is a matrix decomposition method. It aims to reduce the input matrix to a lower rank matrix which is believed to be close representation the original matrix.

3. Linear Discriminant Analysis (LDA) - This is a dimensionality reduction technique which is also sometimes used as a classification algorithm. 

## Ensemble Learning

Ensemble Methods are great way to improve the model performance. These techniques combine results from multiple models in order to achieve this. There are two types of ensemble Methods i.e. **Bagging and Boosting**.

1. Bagging - These methods use models that run independent of each other and combine outcomes to give more credibility to the results.
These are known to be parallel methods. **RandomForest** is a very common example of Bagging Method.

2. Boosting - These methods are sequential in nature and use errors from previous model as a way of improving next model.

## Deep Learning

Deep Learning is the branch of Machine Learning where we deal with Neural Networks. The structure of Neural Networks are supposed to be a replication of human brain and are alternatives to the techniques mentioned above. We will not go into details of this section as of now.

The techniques mentioned in this post are not exhaustive but contains commonly used algorithms. I will be attempting to describe each of these in separate posts.




