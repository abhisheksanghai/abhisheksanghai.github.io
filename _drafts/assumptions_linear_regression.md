---
layout: post
comments: true
title: "Assumptions of Linear Regression"
date: 2019-06-29
---

In the last post, I described the inner workings of a Linear Regression Model. Now, with any model there is an randomness associated which we call the noise in the data. Usually, we can represent it as **Data = Formula + Noise**. For us to understand how good our model is, we should explore this noise for any improvements possible.

Linear Regression - **(insert here)**

Let's list down the assumptions that we should be checking in case of a Linear Regression Model:
1. Linearity - The independent variables should be having a linear relationship with the dependent variable. This is inherently because we are trying to build a linear model and any non linearity would not be taken into account by our linear equation. This assumption is verified by simply looking at the scatter plot between the variables.

**insert Scatter Plot for 2 linear related variables**

In case we find any non linear relationship appearing in the scatter plot, it should be used to apply transformations on the independent variable.

**insert non linear graph**

From above plot its pretty obvious that there is a non linear relationship present. Hence the transformation should be - 

**insert transformed graph**

Now, we are good to include the variable in the model.

2. Normality of Residuals - The residuals of a linear regression model are supposed to follow normal distribution by mathematical definition. This can be checked by looking the the histogram of residuals from the model. 

**insert histogram of normal distribution**

In case we dont get a normal distribution out of the histogram, it means the confidence intervals we get would not be much reliable but the model can still be considered pretty good for predictions.

3. Constant Error Variance of Residuals (Homoscedasticity) - The Residuals are also expected to be uniformly distributed across the data. This can checked by plotting residuals against the fitted values.

**insert graph**

if the variance of error is not constant, it means there is a scope of improvement in the model and we are missing out on an important factor. **improve this**

An ideal grpah would look something like this.

**insert ideal graph**

4. Independence of Residuals - The basic assumption of this model is that the observations are not correlated with each other. This means if value a particular data point is high, value for subsequent data points will also be high or vice versa for lower values. This can be checked by evaluating autocorrelation for the dependent variable or plotting residuals of the model in the order they appear in the data.

**insert graph**

In case we find a pattern appearing in this graph, that means there is a correlation present in the data and we should be using time series models instead.

Apart from these assumptions we should also check for multicollinearity present in the data.

**Enter Mulicollinaerity Details**


