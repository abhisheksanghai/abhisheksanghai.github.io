---
layout: post
comments: true
title: "Linear Regression"
date: 2019-06-18
---

Linear Regression model is used to obtain relationship between a continuous outcome variable and one or more predictor variables. It is generally a good practice to understand the intution behind this approach. On the algorithm front, there are two techniques commonly used to optimize the parameters of the model, Normal Equation Method (uses Linear Algebra) and Gradient Descent (uses differential calculus, commonly used in a lot of Machine Learning Models). 

### Intution

General equation for linear regression with n independent variables is, 

Y(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub>x<sub>1</sub> + &theta;<sub>2</sub>x<sub>2</sub> + ... + &theta;<sub>n</sub>x<sub>n</sub> + &epsilon;

and the prediction equation is, 

Y&#770;(x) = h<sub>&theta;</sub>(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub>x<sub>1</sub> + &theta;<sub>2</sub>x<sub>2</sub> + ... + &theta;<sub>n</sub>x<sub>n</sub> 

_where_, Y is actual dependent variable, 
x<sub>1</sub>, x<sub>2</sub>, .... , x<sub>n</sub> are independent variables, 
h<sub>&theta;</sub>(x) is predicted dependent variable,
&theta;<sub>o</sub>, &theta;<sub>1</sub>, ... , &theta;<sub>n</sub> are coefficients of independent variables and
&epsilon; is the error term.

The error metric considered here is Sum of Square of Error (SSE) because of which the model is also known as Ordinay Least Square (OLS). Our objective is to minimize SSE in order to reach as close to Y as possible.

SSE = &Sigma;(h<sub>&theta;</sub>(x) - Y(x))<sup>2</sup> = &Sigma;(&epsilon;)<sup>2</sup>

**_Case 1:_**

Consider the situation where we do not have any independent variables. One of the possible ways of prediction in this case would be to just take the average of Y. This can be suitably depicted using the above equations,

Y&#773; = h<sub>&theta;</sub>(x) = &theta;<sub>o</sub>, where &theta;<sub>o</sub> is a constant.

In this case, SSE is called Sum of Square Total, SST = &Sigma;(Y(x) - Y&#773;)<sup>2</sup> **(also called variance of Y)**

The error SST is considered as a reference for Linear Regression Models to be evaluated as we start including independent variables.
This is because, the error metric is supposed to decline with increase in variables (otherwise including the variable is useless).

**_Case 2:_**

After inclusion of independent variables, the error metric i.e. SSE = &Sigma;(Y(x) - h<sub>&theta;</sub>(x))<sup>2</sup> = &Sigma;(Y(x) - Y&#770;(x))<sup>2</sup>

Intutively, SST is the error of Y with no independent variable (Total variance) while SSE is the error of Y with independent variables included (Unexplained variance). From this, we can compute the variance that model in _case 2_ is able to explain compared to _case 1_. Let's call it SSR (Sum of Square of Regression also called explained variance). 

So, **SSR = SST - SSE**

![Linear Regression](/images/Linear_Regression/Linear_Regression.jpg)

Now we can define another evaluation metric for our model i.e. R-Squared = (Explained Variance)/(Total Variance)

R<sup>2</sup> = SSR/SST = (SST - SSE)/SST = 1 - (SSE/SST)

R<sup>2</sup> varies between 0 and 1. Higher the R<sup>2</sup> &#8658; better the model. **(Caution! Overfitting)**

Mathematically, R<sup>2</sup> may have negative values. However, when this happens, the error of the model is greater than SST, so the predicitons are worse than the average predictions with no independent variables and model is useless. This situation might arise in certain cases of overfitting when validating model with test data.

### Overfitting

Once the model is built on the data (called as train data), we have to test it against unseen or out of sample data (called as test data) to verify that the patterns or equations discovered apply to them as well. Often, it so happens that while trying to learn the relationship, we end up learning the noise present in the data as well. This leads to really good results for the train data but when applied to test data, the result declines. 

In order to prevent overfitting, instead of relying on R<sup>2</sup> alone (R<sup>2</sup> will always increase as we increase no. of variables), a new metric is designed, **Adjusted R-Squared**.

Adj R<sup>2</sup> = 1 - <sup>(1 - R<sup>2</sup>)*(n - 1)</sup>&frasl;<sub>(n - p - 1)</sub>, _where_, n is no. of data points and p is no. of variables.

From the equation above, as p increases (Keeping R<sup>2</sup> constant) &#8658; Adj R<sup>2</sup> decreases, but 
since we know that as p increases &#8658; R<sup>2</sup> increases, and from the equation again, as R<sup>2</sup> increases &#8658; Adj R<sup>2</sup> increases.
So, it's a battle between p and R<sup>2</sup> that will decide if  Adj R<sup>2</sup> will increase or decrease. If increase in p does not increase R<sup>2</sup> to a certain limit, Adj R<sup>2</sup> decreases. Hence, Adj R<sup>2</sup> is often used as the metric to come up with optimum list of variables in the final model.

### Theory

- **Normal Equation Method** - 

This method is based on Linear Algebra. 

Y = X&beta; + &epsilon;

Matrix Representation - 

![Normal_Equation](/images/Linear_Regression/Normal_Equation.PNG)

So, &epsilon; = Y - X&beta;

Now, our error metric SSE can be represented in matrix form as, &epsilon;&#884;&epsilon; = &epsilon;<sub>1</sub><sup>2</sup> + &epsilon;<sub>2</sub><sup>2</sup> + ... + &epsilon;<sub>n</sub><sup>2</sup> = &Sigma;&epsilon;<sub>i</sub><sup>2</sup>

Therefore, &epsilon;&#884;&epsilon; = (Y - X&beta;)&#884;(Y - X&beta;)

&#8658; &epsilon;&#884;&epsilon; = Y&#884;Y - Y&#884;X&beta; - &beta;&#884;X&#884;Y + &beta;&#884;X&#884;X&beta;

Here, 2nd and 3rd term on the RHS are transpose of each other. Also, they are scalar values with dimension (1 x 1). So, they are equal to each other.

&#8658; &epsilon;&#884;&epsilon; = Y&#884;Y - 2&beta;&#884;X&#884;Y + &beta;&#884;X&#884;X&beta;

Now, the above equation is a function of &beta; and our objective is to minimize it. In order to do this, we differentiate the equation with respect to &beta; and equate to Zero.

&#8658; <sup>&#x2202;(&epsilon;&#884;&epsilon;)</sup>&frasl;<sub>&#x2202;&beta;</sub> = -2X&#884;Y + 2X&#884;X&beta; = 0

&#8658; X&#884;X&beta; = X&#884;Y

Now, Pre multiplying by inverse of X&#884;X

&#8658; (X&#884;X)<sup>-1</sup>X&#884;X&beta; = (X&#884;X)<sup>-1</sup>X&#884;Y 

&#8658; I&beta; = (X&#884;X)&#884;X&#884;Y ; where I is the identity matrix

**&#8658; &beta; = (X&#884;X)<sup>-1</sup>X&#884;Y**

If we analyze the above equation, the first term X&#884;X is the covariance matrix of independent variables while second term X&#884;Y is covariance between X and Y. This can be easily seen when we consider the variables in their standardized form (Standard Normal Distribution).

- **Gradient Descent** - 

Gradient tells us the slope of a function at a given position. **It is a vector which always points towards the maximum increase of a function**. So, the general procedure is to define the objective function, randomly initialize parameters and gradually move in the opposite direction as that of the gradient in order to minimize the function's value.

![Gradient Descent](/images/Linear_Regression/Gradient_Descent.jpg)

The Objective function we have is SSE. Let's denote it by J(&theta;) = <sup>1</sup>&frasl;<sub>2n</sub>&Sigma;{h<sub>&theta;</sub>(x<sup>(i)</sup>) - Y<sup>(i)</sup>}<sup>2</sup>; _where_ i = 1 to n. n is no. of observations and k is no. of variables.

The function is same as the one considered before with slight additions.
The additional term 1&frasl;2 is for mathematical convenience while n is merely to make the error metric MSE(Mean Square Error). This would not affect the output that we get.

Gradient of J is defined as, <sup>&#x2202;J(&theta;)</sup>&frasl;<sub>&#x2202;&theta;<sub>j</sub></sub> = <sup>1</sup>&frasl;<sub>n</sub>&Sigma;{h<sub>&theta;</sub>(x<sup>(i)</sup>) - Y<sup>(i)</sup>}x<sup>(i)</sup><sub>j</sub>; _where_ j = 0 to k.

The update equation for &theta;,

Repeat untill Convergence,
&theta;<sub>j</sub>:= &theta;<sub>j</sub> - &alpha;<sup>&#x2202;J(&theta;)</sup>&frasl;<sub>&#x2202;&theta;<sub>j</sub></sub>; _where_ &alpha; is learning rate. 

&alpha; is a hyperparameter that varies between 0 and 1 and needs to be optimized. After every update we calculate J(&theta;) and observe the change. This updation of &theta; might go on forever, so, we define a stopping criteria (often called precision) for when we are very close to the global minima of the function. If the change is less than the specified precision i.e. convergence is achieved, the algorithm stops.

**Note:** The update for all the &theta;s happen simultaneously.

The process described above is called **Batch Gradient Descent**.

An alternate process is **Stochastic Gradient Descent** where we update &theta;s based on 1 data point at a time. The data points are chosen randomly(stochastic). Another alternate approach is **Mini Batch Gradient Descent** where we update &theta;s based on certain fixed no. of data points at a time.

**Python Code** 

- [Batch Gradient Descent](https://github.com/abhisheksanghai/Machine-Learning-Codes/blob/master/codes/Batch-Gradient-Descent-Linear-Regression.md)

I will write a separate post explaining the [Assumptions of Linear Regression](https://abhisheksanghai.com/2019/07/14/assumptions_linear_regression) and its [usage on a dataset]
(Algorithms_in_Action/Linear_regression.ipynb).
