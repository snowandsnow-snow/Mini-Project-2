# Mini-Project-2
The objective of this project is to identify clients who will subscribe (yes/no) for a term deposit.
## 1. Exploratory Data Analysis (EDA)
1. In the downloaded csv dataset, Fistly use "," to divide the data into different columns.
2. Replcae all "." in data or column name to "-" since the code reported error to "."
###  Missing data
There are no missing data but the categoty "unknown" existing in some varaibles
### Univariate patterns
For Numerical Variables: 
* Except 'AGE' is near normal distributed, all other variables are not normal distributed.
* These variables will be grouped into two categorices according to their distribution:
1. PDAYS
2. EURIBOR3M
* Others will be normalized using 'StandardScaler'.
* For Categorical Variables:
For some caterical variables which have too many categories but very unbalanced, they will be grouped into less categories:
1. education: college VS. non-college
2. month :special months (Mar. & Sep. & Otc. & Dec) VS. others
### Bivariate analysis of target versus categorical input variables
Compare the target variale (yes/no) for each category of each variable using bar plot.
### Bivariate analysis of target versus numerical input variables
Compare the target variale (yes/no) for each variable using histogram.

### Transform
Try log transformation for some varible but only duration eliminetd some skew problem. But the log(duration) resulted in bad model results so finally give up.
### Correlations-colinearity problem
Accoring to this guidline,collinarity problem exist in these pairs:
* Emp_var_rate VS. cons_price_idx
* Emp_var_rate VS.euribor3m
* Emp_var_rate VS. nr_employed
* euribor3m VS. cons_price_idx
* euribor3m VS. nr_employed
* Pdays VS. previous

Deal with these two variables to solve collinearity problem:
* Emp_var_rate: remove it in modeling building
* euribor3m: change it to categorical variabe including two groups
* Pdays : change it to categorical variabe including two groups 


## 2. Prepare Data for Machine Learning
### StringIndexer, OneHotEncoderEstimator, OneHotEncoderEstimator, LabelIndexer, StandardScaler
### K-means Clustering
4 clusters were divided using K means method.
## 3. Train/Test split
train: test = 0.8:0.2
## 4. Confusion Matrix
## 5 Supervised Models
### Model # 1: Logistic Regression
* Accuracy-Logistic Regression:  0.903037667071689
* Test Area Under ROC-Logistic Regression: 0.92004
### Model # 2: Decision Tree
 * Accuracy-Decision Tree :   0.9087
 * Test Area Under ROC-Decision Tree: 0.6453
### Model # 3: Random Forest
* Accuracy-Random Forest :  0.8995
* Test Area Under ROC -Random Forest 0.9166
### Model # 4: Gradient-boosted tree
* Accuracy-Gradient-boosted tree :  0.9086
* Test Area Under ROC-Gradient-boosted tree 0.9307
###  Model # 5: Factorization machines classifier
* Accuracy-Factorization machines classifier :  0.9011
* Test Area Under ROC-Factorization machines classifier 0.9101
### Findings and benefits of the champion model
The best mode is gradient-boosted tree. The reason may be because its sampling method and we train them to correct each other's errors, they're capable of capturing complex patterns in the data.
## 6. Best Model Saving and Load for future use
The best supervised model is Gradient-boosted tree with 93.07% AUC and 90.86% accuracy.
Gradient-boosted tree model will be chosen and saved as the champion since it performed best compared with other four models
## 7. Prescriptive recommendations
Based on the decriptive analysis, we have seen a higher subscribe rate among:

* Highly educated
* Single people
* Special months (Mar. & Sep. & Otc. & Dec)
To capitalize on that, we should focus advertising on that demographic with targeted advertising in special months (Mar. & Sep. & Otc. & Dec)s, highly educated and single people
