---
layout: post
comments: true
title: "Algorithms in Machine Learning"
date: 2019-05-21
---

Model refers to a rule, equation or a structure that helps a machine take decisions. Machine Learning (ML) models are in general, a tool useful to establish relationships or find patterns in the data. But as all the good things come with caution, so does Machine Learning. As it is wisely said, all models are wrong, only some are useful. The results from the models should always be verified to make sense from the business perspective.
ML is majorly divided into two types namely, **supervised and unsupervised learning**. **Reinforcement Learning** has emerged as the new section in recent times.

## Supervised Learning

In supervised learning, we have the outcome defined in the form of a variable and the objective is to reach as close as possible to this outcome variable (dependent variable). For this purpose, we use a lot of external information that might help us determine what the value of this outcome variable could be. We call these extrenal factors as predictors or independent variables. These models are of two types i.e. **Regression and Classification**. For achieving our objective, we define an error metric and try to minimize it.

Regression Models have continuous variable as outcome while classification Models are defined for categorical outcome variables.

### Regression Models

1. Linear Regression - It is the most prominent of the Regression models and forms the foundation of machine learning. These models 
are in the form of a linear equation,  y = &theta;x + c, where y is the dependent variable, x is the independent variable. Once this equation is obtained by minimizing an error metric, we try and use it for prediction.

2. Polynomial Regression - This is an alternate form of Linear Regression where the independent variables have degrees associated with  them. Think of it as having multiple variables such as x, x<sup>2</sup> etc.

3. CART (Classification and Regression Trees) - This is a decision tree form of model which takes rule based approach for reaching the objective.

A lot of times, the predictions turn out pretty accurate for the data, model was built on, but it fails to give good results for out of sample data. This phenomena is called **overfitting**. This happens because the model alongwith learning the required pattern in the data, learns the noise in the data as well. So, if the out of sample data does not have the noisy pattern, its prediction will be bad.

One way to deal with this is regularization. Regularization allows us to add a penalty parameter that slightly alters our objective function and doesn't allow us to reach the true minimum and in turn prevents the model from learning noise in the data. Following are different types of regularization for Linear Regression - 

- Lasso Regression or L1 Regularization
- Ridge Regression or L2 Regularization
- Elastic Net Regression

### Classification Models

1. Logistic Regression - It is a classification technique which gives out probability of an event ocuuring based on a transformed linear equation. The probability is then used for taking the decision.

2. Decision Tree - These are tree based approaches that gives out a set of rules to determine the output. There are multiple algorithms 
used for decision tree.

3. SVM (Support Vector Machine) - The principal for these models are, if an outcome variable is linearly inseparable in lower dimension, it can be transformed to a higher dimension and made linearly separable. This is achieved through the help of kernels.

4. Naive Bayes - These are probability based classifiers that works on extended bayes theorem.

5. K-NN Classification - In these models, we look for value of k nearest neighbours in order to make a decision.

Let's move onto Usupervised Learning now.

## Unsupervised Learning

These models do not have any outcome variables defined,rather, they are majorly used for segmenting data into unknown groups with similar characteristics. All the **Clustering Models** fall under this category. **Association Rules** and **Dimensionality Reduction** are also considered as Unsupervised Learning.

(to be updated)




