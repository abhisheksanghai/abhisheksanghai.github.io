---
layout: post
comments: true
title: "Assumptions of Linear Regression"
date: 2019-06-29
---

In the last post, I described the workings of a Linear Regression Model. Now, with any model there is a randomness (error or residual) associated which we call the noise in the data. Usually, we can represent it as **Data = Formula + Noise**. For us to understand how good our model is, we should explore this randomness for any improvements possible.

General equation for linear regression with n independent variables is, 

Y(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub>x<sub>1</sub> + &theta;<sub>2</sub>x<sub>2</sub> + ... + &theta;<sub>n</sub>x<sub>n</sub> + &epsilon;

Following are the assumptions that we should be checking in case of a Linear Regression Model:

1. Linearity - The independent variables should be having a linear relationship with the dependent variable. This is inherently because we are trying to build a linear model and any non linearity would not be taken into account by our linear equation. The implications can be serious deflections of predictions from actual values when model is used to extrapolate beyond range of data model was built on. This assumption can be verified by simply looking at the scatter plot between the variables.

![Scatter Plot Non Linear](/images/Assumptions_Linear_Regression/Scatter_plot_non_linear.png)

In case we find any non linear relationship appearing in the scatter plot like the one above, it should be used to apply transformations on the independent variable. Here, since the relationship appears quadratic, we will apply square root on the independent variable and check the scatter plot once again.

![Scatter Plot Non Linear](/images/Assumptions_Linear_Regression/Scatter_plot_linear.png)

Since, now the relationship is linear, we are good to include the variable in the model.

2. Normality of Residuals - The residuals of a linear regression model are supposed to follow normal distribution by mathematical definition. This can be checked by looking at the histogram of residuals from the model. 

Histogram, Q-Q Plot, Kolmogorov-Smirnov test

**insert histogram of normal distribution**

In case we dont get a normal distribution out of the histogram, it means the confidence intervals we get would not be much reliable but the model can still be considered pretty good for predictions.

3. Constant Error Variance of Residuals (Homoscedasticity) - The Residuals are also expected to be uniformly distributed across the data. This can checked by plotting residuals against the fitted values.

**insert graph**

if the variance of error is not constant, it means there is a scope of improvement in the model and we are missing out on an important factor. **improve this**

An ideal graph would look something like this.

**insert ideal graph**

4. Independence of Residuals - The basic assumption of this model is that the observations are not correlated with each other. This means if value of a particular data point is high, value for subsequent data points will also be high or vice versa for lower values. This can be checked by evaluating autocorrelation for the dependent variable or plotting residuals of the model in the order they appear in the data.

Durbin Watson Test

**insert graph**

In case we find a pattern appearing in this graph, that means there is a correlation present in the data and we should be using time series models instead.

Apart from these assumptions we should also check for multicollinearity present in the data.

**Enter Mulicollinaerity Details**


