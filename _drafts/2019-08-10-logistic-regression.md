---
layout: post
comments: true
title: "Logistic Regression"
date: 2019-05-03
---

Logistic Regression Model is one of the most popular algorithms and is used widely in the industry. It is a classification model that gives out probability of occurence of an event. For eg, if you want to determine, if a customer is going to default on his loan from a bank based on his historical behaviour, logistic regression is one of the models you would be using. 

Since, it is a classification technique, it is used for categorical target variables. 

### Theory

Below is a scatter plot for a continuous predictor and a categorical target variable-

**insert graph**

From the plot it is very obvious that a linear equation like model (linear regression) would not work in it's raw form as the output of linear regression would be unbounded and we would need some sort of transformation to bring the output in the permissible range of probability i.e. (0,1). In case of logistic regression, we use logit transformation for this purpose.

General Equation of a logistic regression with n independent variables - 

P(x) = 1/(1+e<sup>-Y(x)</sup>); 
_where_
Y(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub>x<sub>1</sub> + &theta;<sub>2</sub>x<sub>2</sub> + ... + &theta;<sub>n</sub>x<sub>n</sub>, 

x<sub>1</sub>, x<sub>2</sub>, .... , x<sub>n</sub> are independent variables, 
&theta;<sub>o</sub>, &theta;<sub>1</sub>, ... , &theta;<sub>n</sub> are coefficients of independent variables and
P(x) is the probability of occurence of event.

### Probability (Revision)

The probability of occurence of an event E, is defined as, P(E) =  Favourable Outcomes/ Total Possible Outcomes.

In probability, it's very important to define the sample space (Total possible outcomes). It is represented as S.

So, P(E) = n(E)/n(S)

Eg - Event is Rolling a dice and getting a 4. There is total 6 faces on the dice with numbers 1 to 6 on it.
So, favourable outcome is when we get 4 i.e. 1 case and total possible outcomes is 6. This means, P(4 on dice) = 1/6.

There are some terms that one should be aware of when discussing probability.

1. Exhaustive Events - The set of events that forms the sample space i.e. no event can take place outside this set.

2. Mutually Exclusive Events - Events that do not take place together.

Sum of probabilites of events that are mutually exclusive and exhaustive is 1 

i.e. &Sigma; P(E<sub>i</sub>) = 1 _where_ i = 1,2,3,..,n(S)

3. Independent Events - If occurence of non occurence of an event A does not affect the occurence of another event B, then A and B are said to be independent events.







* when to use - used for categorical variables - 
* probability basics
* difference from linear regression
* equation - 
* explaining the equation
* Odds and odds ratio
* likelihood
* cost function
* derivation
* usage

- look at scatter plots (looks wierd) (exlpains a reason for why not linear)
- probability review
- odds = P(occuring)/P(not occuring)  =p/(1-p), if 1:1 => odds are even
- odds ratio - ratio of odds = odds1/odds0 = 2.33:1/1:1 => odds of getting head on loaded coin 2.33 times higher than odds in fair coin
  odds ratio for a variable represent how the odds change with unit change in variable keeping others constant.
  unit increase in weight increases odds of sleep apnea by 1.07 times which is 7%. Holds true at any given point of weight.
  probability and odds different
- dependent variable is as bernoulli trial, P(S) = pand P(F) = 1-p
- In logistic Regression, we are estimating unknown p for any given linear combination of independent variables
- link to bernoulli to independent variables is called logit (natural log of odds ratio) = ln(p/(1-p))
- Inverse logit - 1/1+e^-alpha => Sigmoid Curve (S curve)
- Odds Ratio from Model (check this) Brandon Foltz video 4




