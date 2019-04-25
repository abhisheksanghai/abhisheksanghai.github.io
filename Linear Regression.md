### Linear Regression

Linear Regression model is used to obtain relationship between a continuous outcome variable and one or more predictor variables. It is generally a good practice to understand the intution behind this approach. On the algorithm front, there are two techniques commonly used to optimize the parameters of the model, Normal Equation Method (uses Linear Algebra) and Gradient Descent (uses differential calculus, commonly used in a lot of Machine Learning Models). 

**Intution**

General equation for linear regression with n independent variables is, 

Y(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub>x<sub>1</sub> + &theta;<sub>2</sub>x<sub>2</sub> + ... + &theta;<sub>n</sub>x<sub>n</sub> + &straightepsilon;

and the prediction equation is, 

Y&#770;(x) = h<sub>&theta;</sub>(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub>x<sub>1</sub> + &theta;<sub>2</sub>x<sub>2</sub> + ... + &theta;<sub>n</sub>x<sub>n</sub> 

_where_, Y is actual dependent variable, 
x<sub>1</sub>, x<sub>2</sub>, .... , x<sub>n</sub> are independent variables, 
h<sub>&theta;</sub>(x) is predicted dependent variable,
&theta;<sub>o</sub>, &theta;<sub>1</sub>, ... , &theta;<sub>n</sub> are coefficients of independent variables and
&straightepsilon; is the error term.

The error metric considered here is Sum of Square of Error (SSE) because of which the model is also known as Ordinay Least Square (OLS). Our objective is to minimize SSE in order to reach as close to Y as possible.

SSE = &Sigma;(h<sub>&theta;</sub>(x) - Y)<sup>2</sup>

_Case 1:_

Consider the situation where we do not have any independent variables. One of the possible ways of prediction in this case would be to just take the average of Y. This can be suitably depicted using the above equations,

Y&#773; = h<sub>&theta;</sub>(x) = &theta;<sub>o</sub>, where &theta;<sub>o</sub> is a constant.

In this case, SSE is called Sum of Square Total, SST = &Sigma;(Y(x)-Y&#773;)<sup>2</sup> **(also called variance of Y)**

The error SST is considered as a reference for Linear Regression Models to be evaluated as we start including independent variables.
This is because, the error metric is supposed to decline with increase in variables (otherwise including the variable is useless).

_Case 2:_

After inclusion of independent variables, the error metric i.e. SSE = &Sigma;(Y(x)-h<sub>&theta;</sub>(x))<sup>2</sup> = &Sigma;(Y(x)-Y&#770;(x))<sup>2</sup>

Intutively, SST is the max error of Y with no independent variable (Total variance) while SSE is the error of Y with independent variables included (Unexplained variance). From this, we can compute the variance that model in _case 2_ is able to explain compared to _case 1_. Let's call it SSR (Sum of Square of Regression also called explained variance). 
So, **SSR = SST-SSE**

Now we can define another evaluation metric for our model i.e. R-Squared = (Explained Variance)/(Total Variance)

R<sup>2</sup> = SSR/SST = (SST-SSE)/SST = 1-(SSE/SST)

R<sup>2</sup> varies between 0 and 1. Higher the R<sup>2</sup> => better the model. **(Caution! Overfitting)**

Mathematically, R<sup>2</sup> may have negative values. However, when this happens, the error of the model is greater than SST, so the predicitons are worse than the average predictions with no independent variables and model is useless.

**Overfitting**

Once the model is built on the data (called as train data), we have to test it against unseen or out of sample data (called as test data) to verify that the patterns or equations discovered apply to them as well. Often, it so happens that while trying to learn the relationship, we end up learning the noise present in the data as well. This leads to really good results for the train data but when applied to test data, the result declines. 

In order to prevent overfitting, instead of relying on R<sup>2</sup> alone (as R<sup>2</sup> will always increase as we increase no. of variables), a new metric was designed, Adjusted R-Squared.

Adj R<sup>2</sup> = 1 - <sup>(1-R<sup>2</sup>)*(n-1)</sup>&frasl;<sub>(n-p-1)</sub>, _where_, n is no. of data points and p is no. of variables.

Looking at the equation, as p increases => R<sup>2</sup> increases => Adj R<sup>2</sup> increases,
On the other hand, as p increases => Adj R<sup>2</sup> decreases.
So, if increase in p does not increases R<sup>2</sup> as it should, Adj R<sup>2</sup> will decrease. Hence, Adj R<sup>2</sup> is often used as the metric to come up with optimum list of variables in the final model.

**Theory**

_To be updated_

**Code** 
- Gradient Descent

```
import numpy as np
import pandas as pd

class LinearRegression_Self:

    #get data
    def __init__(self,data,x_index,y_index):
        self.data = data #data
        self.x = data.iloc[:,x_index] #independent variables
        self.y = data.iloc[:,y_index] #dependent variable
        
    #get parameters    
    def fit(self,precision,learning_rate,max_iter):
        n_var = self.x.shape[1] #no. of variables
        n_obs = self.x.shape[0] #no. of observations
        theta = np.ones((n_var + 1)) #initializing parameters
        iters = 0 #initialize counter for iterations
        diff = 1 #initial values for change in objective function
        self.x = np.append(np.ones((n_obs,1)), self.x, axis=1) #include constant variable for constant term in equation
        J_new = (0.5/n_obs)*sum((np.array([sum([self.x[j,i]*theta[i] for i in range(n_var+1)]) for j in np.arange(n_obs)])-self.y)**2) # Evaluate Objective function
        while diff > precision and iters <= max_iter:
            J_curr = J_new
            dJ = np.array([(1/n_obs) * sum((np.array([sum([self.x[j,i]*theta[i] for i in range(n_var+1)]) for j in np.arange(n_obs)])-self.y)*self.x[:,i]) for i in np.arange(n_var+1)]) #gradient of objective function
            theta = theta - (learning_rate/n_obs)*dJ #Update parameters
            J_new = (0.5/n_obs)*sum((np.array([sum([self.x[j,i]*theta[i] for i in range(n_var+1)]) for j in np.arange(n_obs)])-self.y)**2) #Re-evaluate Objective function
            diff = abs(J_curr - J_new) #Update change in objective function value
            iters += 1 #update iteration no.
            print("Objective Function for Iteration ",iters," is ",J_new)
        return(theta) #Return Parameters 

```
