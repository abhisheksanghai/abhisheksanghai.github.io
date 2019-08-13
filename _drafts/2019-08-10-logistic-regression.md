---
layout: post
comments: true
title: "Logistic Regression"
date: 2019-05-03
---

* when to use - used for categorical variables
* probability basics
* difference from linear regression
* equation
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




