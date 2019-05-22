---
layout: post
comments: true
title: "Algorithms in Machine Learning 2.0"
date: 2019-05-22
---


Let's move onto Usupervised Learning now.

## Unsupervised Learning

These models do not have any outcome variables defined,rather, they are majorly used for segmenting data into unknown groups with similar characteristics. All the **Clustering Models** fall under this category. **Association Rules** and **Dimensionality Reduction** are also considered as Unsupervised Learning.

### Clustering

Clustering refers to dividing a population into multiple groups such that the the data points in the same group are more similar to each other than other groups.

1. K-Means Clustering - These models work with euclidian distance between data points to form clusters and are the most preferred method for clustering. 

2. Agglomerative Hierarchical Clustering - In this technique, we first consider all the data points as individual clusters and then keep combining them one by one based on similarity. The output is represented through a tree like diagram called Dendogram. 

### Association Rules

1. Apriori Algorithm - This is a probabilty based algorithm and is primarily used for Market Basket Analysis where we look for products often bought together and then form product bundles.

### Dimensionality Reduction

Often in model building exercise, we find ourselves dealing with far more no. of variables than we can use in the model. It leads to a situation where we either drop variables or combine them together to come up with a new variable. The techniques involving combination of variables comes under this section.

1. Principal Component Analysis (PCA) - This technique combines n variables and gives out new variables with the objective of maximising the variance in the data so that the loss of information is minimal. PCA can be used for feature extraction as well.

2. Singular Value Decomposition (SVD) - This is a matrix decomposition method. It aims to reduce the input matrix to a lower rank matrix which is believed to be close representation the original matrix.

3. Linear Discriminant Analysis (LDA) - This is a dimensionality reduction technique which is also sometimes used as a classifiation algorithm. 

**Neural Networks**

Now that we have these out of the way, let's talk about Ensemble Learning
## Ensemble Learning

1. Bagging

2. Boosting




