# Bank Marketing — Model Report

## 1. Purpose
The bank wants to find clients who are more likely to open a term deposit. The call center can contact only 10% of clients.

## 2. Data
I used the provided Bank Marketing training data. The target variable is `y` (yes or no). It shows whether a client agreed to open a term deposit.

I did not use `id` because it is only a client identifier. I also did not use `duration` because it is not available before the call and is not included in `test.csv`.

## 3. Data Preprocessing
The categorical data contain `unknown` values. I kept them as a separate category. Replacing them with the most common values gave almost the same results.

The value `pdays = 999` means that the client was not contacted before. In the pipeline, I treat 999 as a missing value, replace it with the median of real `pdays` values, and add a separate indicator.

## 4. Model Selection
I kept 20% of the data for final evaluation. All previous comparisons used the remaining 80%.

I compared Logistic Regression, Decision Tree, and Linear SVM. Logistic Regression and Linear SVM gave similar results. I chose Logistic Regression because it is stable and easy to explain.

## 5. Results
The model selected 658 clients for calls on the hold-out data.

- 341 selected clients agreed to open a term deposit.
- 317 selected clients did not agree.
- 401 potential clients were missed because the call center could not contact everyone.

## 6. Final Model
The final saved model is a scikit-learn Pipeline. It accepts the original features from `test.csv` without manual preprocessing.

## 7. Limitations
The data are historical, so the results may be different for future clients. The model should be checked regularly to see whether its predictions remain useful.