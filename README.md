# Machine Learning

ML models are a tool useful to establish a relationship or find patterns in the data. As it is wisely said, all models are wrong, only some are useful. The results from the models should always be verified to make sense from the business perspective.
ML is majorly divided into two types namely, **supervised and unsupervised learning**.

## Supervised Learning

These are models that have the outcome variable defined and the objective is to reach as close as possible to this outcome variable.
These are of two types i.e. **Regression and Classification**.

Regression Models have continuous variable as outcome while classification Models have categorical variables as outcome.

### Regression Models

1. Linear Regression -

Linear Regression model is used to obtain relationship between a continuous outcome variable and one or more predictor variables. It is generally a good practice to understand the intution behind this approach. On the algorithm front, there are two algorithms commonly used to optimize the parameters of the model, Linear algebra (Specific to this model) and Gradient Descent (commonly used in a lot of Machine Learning Models). 

_Intution_

General equation for linear regression with n independent variables is, 
Y(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub>x<sub>1</sub> + &theta;<sub>2</sub>x<sub>2</sub> + ... + &theta;<sub>n</sub>x<sub>n</sub> + &straightepsilon;

h<sub>&theta;</sub>(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub>x<sub>1</sub> + &theta;<sub>2</sub>x<sub>2</sub> + ... + &theta;<sub>n</sub>x<sub>n</sub> 

where Y is actual dependent variable, x<sub>1</sub>,x<sub>2</sub>,....,x<sub>n</sub> are independent variables and h<sub>&theta;</sub>(x) is predicted dependent variable

Now, if we do not have any independent variables, the equation would become,
Y = b0
i.e. the prediction is a constant which is average of Y.

The error metric considered is Sum of Square of Error (SSE).
In this case, it is called Sum of Square of Total, SST = sum((y-y_avg)^2) **(also called variance of Y)**

As we start including independent variables, the error is supposed to decline (otherwise including the variable is useless)

After inclusion of independent variables, the error i.e. SSE = sum((y-y_pred)^2)

Intutively, SST is the total variance (error) of Y while SSE is the variance (error) that the model is still not able to explain after inclusion of independent variable. From this, we can compute the error that the new model is able to explain. Let's call it SSR (Sum of Square of Regression).
So, SSR = SST-SSE
Now we can define a metric to get the ratio of error expalined by the model.
This metric is called R2 (R-Squared) = SSR/SST = (SST-SSE)/SST = 1-(SSE/SST)

Since, the SSE varies between 0 and SST, R2 varies between 0 and 1. Higher the R2 => better the model.

In very rare cases R2 might be negative. This is when the error is greater than SST, so the predicitons are worse than the average predictions with no independent variables.




**Code** 
- Gradient Descent

```
import numpy as np
import pandas as pd

class LinearRegression_Self:
    
    #get data
    def __init__(self,data,x_index,y_index):
        self.data = data
        self.x = data.iloc[:,x_index]
        self.y = data.iloc[:,y_index]
        
    def fit(self,precision,learning_rate,max_iter):
        n_var = self.x.shape[1]
        n_obs = self.x.shape[0]
        theta = np.ones((n_var + 1))
        iters = 0
        diff = 1
        self.x = np.append(np.ones((n_obs,1)), self.x, axis=1)
        J_new = (0.5/n_obs)*sum((np.array([sum([self.x[j,i]*theta[i] for i in range(n_var+1)]) for j in np.arange(n_obs)])-self.y)**2)
        while diff > precision and iters <= max_iter:
            J_curr = J_new
            dJ = np.array([(1/n_obs) * sum((np.array([sum([self.x[j,i]*theta[i] for i in range(n_var+1)]) for j in np.arange(n_obs)])-self.y)*self.x[:,i]) for i in np.arange(n_var+1)])
            theta = theta - (learning_rate/n_obs)*dJ
            J_new = (0.5/n_obs)*sum((np.array([sum([self.x[j,i]*theta[i] for i in range(n_var+1)]) for j in np.arange(n_obs)])-self.y)**2)
            diff = abs(J_curr - J_new)
            iters += 1
            print("Objective Function for Iteration ",iters," is ",J_new)
        return(theta)

```
