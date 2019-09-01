---
layout: post
comments: true
title: "Logistic Regression"
date: 2019-09-01
---

Logistic Regression is one of the most popular algorithms and is used widely in the industry. It is a classification model that gives out probability of occurence of an event. For eg, if you want to determine if a customer is going to default on his loan from a bank based on his historical behaviour, logistic regression is one of the models you would be using. Since, it is a classification technique, it is used for categorical target variables. 

### Theory

Below is a scatter plot for a continuous predictor and a categorical target variable-

**insert graph**

From the plot it is very obvious that a linear equation like model (linear regression) would not work in it's raw form as the output of linear regression would be unbounded and we would need some sort of transformation to bring the output in the permissible range of probability i.e. (0,1). In case of logistic regression, we use logit transformation for this purpose.

Z(x) = &theta;<sub>o</sub> + &theta;<sub>1</sub>x<sub>1</sub> + &theta;<sub>2</sub>x<sub>2</sub> + ... + &theta;

**Logit Transformation** (also defined as log(odds)), Z(x) = ln(P(x)/(1-P(x))); _where_ ln is natural log.

&#8658; P(x) = 1/(1+e<sup>-Z(x)</sup>); 

_where_ x<sub>1</sub>, x<sub>2</sub>, .... , x<sub>n</sub> are independent variables, 
&theta;<sub>o</sub>, &theta;<sub>1</sub>, ... , &theta;<sub>n</sub> are coefficients of independent variables and
P(x) is the probability of occurence of event.

which is also **General Equation of a logistic regression with n independent variables**. 

**insert output graph for logistic (Sigmoid Curve)**

### Probability (Revision)

The probability of occurence of an event E, is defined as, P(E) =  Favourable Outcomes/ Total Possible Outcomes.

In probability, it's very important to define the sample space (Total possible outcomes). It is represented as S.

So, P(E) = n(E)/n(S)

Eg - Event is Rolling a dice and getting a 4. There is total 6 faces on the dice with numbers 1 to 6 on it.
So, favourable outcome is when we get 4 i.e. 1 case and total possible outcomes is 6. This means, P(4 on dice) = 1/6.

Now, there are some terms that one should be aware of when discussing probability.

1. **Exhaustive Events** - The set of events that forms the sample space i.e. no event can take place outside this set.

2. **Mutually Exclusive Events** - Events that can not take place together.

Sum of probabilites of events that are mutually exclusive and exhaustive is 1 

i.e. &Sigma; P(E<sub>i</sub>) = 1 _where_ i = 1,2,3,..,n(S)

**insert venn diagram**

3. **Independent Events** - If occurence or non occurence of an event A does not affect the occurence of another event B, then A and B are said to be independent events.

In order to understand this better, we have to look for conditional probabillity.

P(A/B) => read as Probability of occurence of event A when it is known that Event B has already occured. (Probability of A given B)

**insert venn diagram**

Since, Event B already occured, the set of possible outcomes now reduced to n(B) and favourable outcomes from these are the ones where A and B occurs simultaneously

So, P(A/B) = P(A&cap;B)/P(B)

Now, P(A) changed after occurence of B => it became P(A/B). What happens when P(A/B) = P(A)?

Intuitively, it means occurence of B did not affect A i.e. B has no effect on A &#8658; A and B are independent events.

Also, P(A&cap;B) = P(A/B)*P(B) 

&#8658; P(A&cap;B) = P(A)*P(B) &#8658; **Condition of Independence**.

This condition of independence can be extended to n no. of events being independent of each other i.e.

&#8658; P(A&cap;B&cap;C) = P(A)*P(B)*P(C) and so on.

Next, Let's talk about **Odds and Odds Ratio**.

- Odds = P(occurence)/P(non occurence)  =p/(1-p)

Eg - For a coint toss, odds of getting a head = P(Head)/P(Not Head) = P(Head)/P(Tail) = 0.5/0.5 = 1:1

- Odds Ratio = Ratio of two odds = Odds1/Odds0

Eg - For a fair coin toss, P(Head) = 0.5 &#8658; Odds(Head) = Odds0 = 1:1

For a loaded unfair Coin, let's say, P(Head) = 0.6 &#8658; Odds(Head) = Odds1 = 0.6:0.4 = 3:2

Therefore, Odds Ratio = Odds1/Odds0 = 1.5

This means, Odds of getting a head on the unfair coin is 1.5 times higher than the fair coin.

**But, Why are we talking about Odds and Odds Ratio all of a sudden?**

That's because in the output of logistic regression, Odds Ratio of a variable can be defined as the increase in odds of Event happening with unit increase in corresponding variable and it remains constant irrespective of the value from which the unit increase has been made. **Note:** Probability might still be less with higher value for Odds Ratio.

### Algorithm

In Logistic Regression, we use Maximum Likelihood Estimation in order to arrive at the coefficients of the variables.

- Maximum Likelihood Estimation - 

The equation we have at hand is, P(x<sup>(i)</sup>) = h<sub>&theta;</sub>(x<sup>(i)</sup>) = 1/(1+e<sup>-Z(x<sup>(i)</sup>)</sup>); _where_ Z(x<sup>(i)</sup>) = &theta;<sup>T</sup>x<sup>(i)</sup>

Now, P(Y=1/x<sup>(i)</sup>;&theta;) = P(x)<sup>(i)</sup> = h<sub>&theta;</sub>(x<sup>(i)</sup>) (This means Y=1, x is known and &theta; is the unkown on which probability depends)

P(Y=0/x<sup>(i)</sup>;&theta;) = 1 - P(x<sup>(i)</sup>) = 1 - h<sub>&theta;</sub>(x<sup>(i)</sup>)

So, together, it can be represented as, P(Y<sup>(i)</sup>/x<sup>(i)</sup>;&theta;) = h<sub>&theta;</sub>(x<sup>(i)</sup>)<sup>Y<sup>(i)</sup></sup> (1 - h<sub>&theta;</sub>(x<sup>(i)</sup>))<sup>(1-Y<sup>(i)</sup>)</sup>

This equation is for a single data point. Now, in any linear model, it is one of the key assumption that the observations will be independent of each other i.e. occurence of event for one data point will not affect the occurence of event for another. Using this assumption, we can apply condition of independence here,

P(Y/x;&theta;) = P(Y<sup>(1)</sup>/x<sup>(1)</sup>;&theta;) * P(Y<sup>(2)</sup>/x<sup>(2)</sup>;&theta;) * P(Y<sup>(3)</sup>/x<sup>(3)</sup>;&theta;) * .... * P(Y<sup>(m)</sup>/x<sup>(m)</sup>;&theta;) ; _where_ m is no. of data points.

P(Y/x;&theta;) = 	&Pi; P(Y<sup>(i)</sup>/x<sup>(i)</sup>;&theta;) _where_ i = 1,2,3,...,m

&#8658; L(&theta;) = &Pi; h<sub>&theta;</sub>(x<sup>(i)</sup>)<sup>Y<sup>(i)</sup></sup> (1 - h<sub>&theta;</sub>(x<sup>(i)</sup>))<sup>(1-Y<sup>(i)</sup>)</sup> _where_ i = 1,2,3,...,m and L(&theta;) is called Likelihood function.

This is our objective function and we are going to try and maximize it and for this we will be using Gradient Ascent(opposite of Gradient Descent) but first we need it in correct form.

So, taking Log on both sides, we get log likelihood which is what we will be maximizing

l(&theta;) = log(L(&theta;)) = &Sigma; Y<sup>(i)</sup> * log(h<sub>&theta;</sub>(x<sup>(i)</sup>)) + (1 - Y<sup>(i)</sup>) * log(1 -h<sub>&theta;</sub>(x<sup>(i)</sup>))

Gradient of l is defined as, <sup>&#x2202;l(&theta;)</sup>&frasl;<sub>&#x2202;&theta;<sub>j</sub></sub> = &Sigma;{Y<sup>(i)</sup> - h<sub>&theta;</sub>(x<sup>(i)</sup>)}x<sup>(i)</sup><sub>j</sub>; _where_ j = 0 to n.

The update equation for &theta;,

Repeat untill Convergence,
&theta;<sub>j</sub>:= &theta;<sub>j</sub> + &alpha;<sup>&#x2202;l(&theta;)</sup>&frasl;<sub>&#x2202;&theta;<sub>j</sub></sub>; _where_ &alpha; is learning rate. 


