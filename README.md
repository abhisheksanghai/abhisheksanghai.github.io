# Machine Learning Algorithms
## Supervised Learning

1. Linear Regression 

**Theory**

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
