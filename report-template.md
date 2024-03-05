# Credit risk analysis report

## Overview of the Analysis

The purpose of the analysis is to train and evaluate a model that can assess the creditworthiness of borrowers using historical lending data from a peer-to-peer lending services company. The goal is to build a model capable of identifying whether loans are "healthy" or "high-risk" based on various financial data points, aiming to effectively predict loan risk.


Given the financial information listed below, I was tasked with predicting `loan_status` as either Healthy `0`, or High-risk `1`.
```
columns = loan_size, interest_rate, borrower_income, debt_to_income,
          num_of_accounts, derogatory_marks, total_debt, loan_status

Total number of records: 77,536
loan_status 0: 75,036
loan_status 1: 2,500
```
### Machine learning process
- Split the Data into Training and Testing Sets
    - Separated `y` to represent loan_status column
    - Separated `X` to represent the features contributing to the target `y`
    - Split original data into training and testing data using `train_test_split()`
- Created a Logistic Regression Model with the Original Data
    - Instantiated and fit a logistic regression model to the training data using `LogisticRegression()`
    - Used `.predict()` based on the training data and compared with testing data (returned `accuracy_score` of `99.24%`)
---

## Results

### Accuracy
A `classifcation_report()` returns that overall accuracy is `99%` with macro and weighted averages across metrics at `94%` and `99%` respectively.

### Precision
#### Healthy loan precision: `100%`
The model predicted `18,746` loans as healthy. `18,679` of those were predicted correctly, leaving `67` as false negatives (high-risk).

#### High-risk precision: `87%`
The model predicted `638` loans as high-risk. `558` of those were predicted correctly, leaving `80` were false positives (healthy).

### Recall scores
#### Healthy loan recall: `100%`
There were `18,759` actual high-risk loans. The model correctly predicted `18,679` of them while missing `80`.

#### High-risk recall: `89%`
There were `625` actual high-risk loans. The model correctly predicted `558` of them while missing `67`.

## Summary

The model is strong at predicting both healthy and high-risk loans. Recall and precision are lower with high-risk loans. From a business perspective, it would seem pertinent to be more cautious than the model currently is with identifying high-risk loans. However, more prudence could negatively impact the customer-experience of healthy loan candidates being misidentified as high-risk.

While this model may serve as helpful to a pre-approval process, I cannot recommend that it be relied on exclusively for automated loan approval or denial.