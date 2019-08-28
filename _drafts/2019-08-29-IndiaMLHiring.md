---
layout: post
comments: true
title: "India ML Hiring"
date: 2019-08-29
---

Recently I partitipated in one of the hackathons organized by Analytics Vidhya "IndiaMLHiring". The way it works is we get a 
training data with target variables and a test data without target variable. The test data received is 40% of the entire test data 
and rest 60% is kept hidden. We are allowed to make submissions and test our model as per accuracy provided by the system. 
These gives us a rank on Public Leaderboard. Once the contest is over, our final marked submission is tested against the remaining 
60% of the test data which is unseen to the model. The results from this gives us a new rank which constitutes Private Leaderboard 
and is the final rank. 

The problem statement involved predicting loan deliquency of borrowers given various parameters. Below is the complete problem statement.

### Problem Statement

Loan Delinquency Prediction is one of the most critical and crucial problem faced by financial institutions and organizations as it 
has a noteworthy effect on the profitability of these institutions. In recent years, there is a tremendous increase in the volume 
of non–performing loans which results in a jeopardizing effect on the growth of these institutions. Therefore, to maintain a healthy 
portfolio, the banks put stringent monitoring and evaluation measures in place to ensure timely repayment of loans by borrowers. 
Despite these measures, a major proportion of loans become delinquent. Delinquency occurs when a borrower misses a payment against 
his/her loan. Given the information like mortgage details, borrowers related details and payment details, our objective is to identify 
the delinquency status of loans for the next month given the delinquency status for the previous 12 months (in number of months).

Submissions are evaluated on F1-Score between the predicted class and observed.

The datasets and the submission code can be found [here](https://github.com/abhisheksanghai/IndiaMLHiring-2019). I used R programming for this hackathon.

### Data Dictionary

- loan_id	- Unique loan ID
- source - Loan origination channel
- financial_institution - Name of the bank
- interest_rate - Loan interest rate
- unpaid_principal_bal - Loan unpaid principal balance (described as initial loan amount)
- loan_term - Loan term (in days)
- origination_date - Loan origination date (YYYY-MM-DD)
- first_payment_date - First instalment payment date
- loan_to_value - Loan to value ratio (described as ratio of loan amount to asset value against which loan was granted)
- number_of_borrowers - Number of borrowers
- debt_to_income_ratio - Debt-to-income ratio (debt includes all the loans the borrower has taken)
- borrower_credit_score - Borrower credit score
- loan_purpose - Loan purpose
- insurance_percent - Loan Amount percent covered by insurance
- co-borrower_credit_score - Co-borrower credit score
- insurance_type - 0 - Premium paid by borrower, 1 - Premium paid by Lender
- m1 to m12 - Month-wise loan performance (deliquency in months)
- m13	(target) - loan deliquency status (0 = non deliquent, 1 = deliquent)

### Data Exploration

The code used for this entire process is present [here](https://github.com/abhisheksanghai/IndiaMLHiring-2019/blob/master/Code.R).

1.	Initially, basic exploration of dataset was done which involves looking at the imbalance in the data, univariate analysis, cross tabulation for categorical variables with m13 and distribution of continuous variables for m13.
2.	Variable Exploration and Feature Engineering - 
  * Source – Use as binary dummy variables.
  * Financial Institution – Clubbed from 19 values to 6 values using response rate and frequency of categories. Post this, binary dummy variables were created for this.
  * Interest Rate – Used as it is.
  * Unpaid Principal Balance – Since, this was to be taken as initial loan amount, couple of new variables were created out of this. 
    * Premium Per Year – Total EMI to be paid if loan term was 1 year considering Simple Interest.
    * Total Premium – Actual EMI to paid if considering Simple Interest
    * Total Premium CI – Actual EMI based on Compound Interest was also calculated but it did not help in results.
  * Loan Term – Loan Term was used as it is. It was calculated in months as well but did not help.
    * Deferral Period (First Payment Duration) – Difference between first payment date and origination date was calculated and found to be either 1, 2 or 3 months.
  * Loan to Value – Since, this was explained as loan amount to actual asset, a new variable was created
    * Collateral – unpaid principal balance/loan to value
  * No. of Borrowers – Used as categorical
  * Debt to income ratio – Since, Debt to income ratio considers all the loans, a new variable was created
    * Debt income by Loan Value – Debt to income ratio / loan to value = %Collateral/%Loan (Ratio of how much collateral belongs to this loan to how much debt is for this loan)
  * Credit Scores – Co-borrower Credit Score is present only where no. of borrowers is two. To make use of this properly in the model, new variables were created and original variables were dropped-
    * Max Credit Score – Out of borrower and co borrower whoever has highest score.
    * Min Credit Score - Out of borrower and co borrower whoever has lowest score.
    * Avg Credit Score – Averaged wherever 2 borrowers are present, and borrowers score wherever only 1 borrower is present
    * Credit Score available – A lot of borrower’s credit score was 0 hinting, there credit score was not available but looking at data, none of them defaulted, hence a new variable. (Whenever 2 borrowers were there and co borrower’s credit score was 0, borrower’s credit score was also 0)
    * An attempt was made to replace 0 credit scores with 840 (highest borrower credit score) but did not yield good results.
  * Loan Purpose – Used as binary dummy variable.
  * Insurance Percent – Used as it is. Also, couple of new variables were created.
    * Insurance Presence – If Loan was insured or not.
    * Loan covered under insurance – Unpaid Principal Amount * Insurance Percent = Amount of loan covered under insurance.
  * Insurance Type – Since, the values are only 0 and 1, used as it is.
  * m1 to m12 – Supposedly, no. of months by which the customer delayed the repayment. Some new variables were created.
    * Max delinquent – max no. of months a customer delayed the payment in last 12 months.
    * No. of months delinquent 12 Months – No. of months in which the customer was delinquent in last 12 months.
    * No. of months delinquent 6 Months – No. of months in which the customer was delinquent in last 6 months.
    * No. of months delinquent 3 Months – No. of months in which the customer was delinquent in last 3 months.
    * Min Delinquent – Min no. of times a customer was delinquent (seemed effective in exploratory analysis but did not improve model)
    * All m1 to m12 were converted to binary variables with exception of m12 as it seemed important in exploratory analysis. New variable for m12 was also created.

### Model Building and Selection - 
  * Initially, logistic regression was used with 5 fold Cross Validation with train cv F1 Score being 0.53, but the leader board score very low (0.29) – Private Leader board Score is 0.60
  * After this, I tried xgboost model with lots of different iterations which did give some improvements train cv score 0.57 to 0.60 for different iterations. Since the train and test data had different cut-offs i.e. 0.33 for train and 0.23 for test giving best F1 Scores, I tired with different cut-offs and settled with cut-off 0.3. Public Scoreboard improved to 0.345
  * SMOTE was used for balancing the dataset with train cv improving significantly to 0.9 but leader board score did not improve beyond 0.34
  * Lot of ensembles were tried with different submissions
  * Final Submission was marked as xgboost with cut-off as 0.3 for delinquency. The model for 5 fold Cross validation with predictions being even if 1 model predicted TRUE instead of majority.
  * Final Parameters - booster="gbtree", eta=0.001, max_depth=5, gamma=3, subsample=0.75, colsample_bytree=1, objective="multi:softprob", eval_metric="mlogloss", num_class=num_class
