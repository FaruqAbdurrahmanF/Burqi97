# Churn (EDA and ML)

## Use Case

### Objective Statement:
- Get business insight into how much churn occurs in the dataset you own
- Get business insight on the percentage of customers churn

### Methodology / Analytic Technique:
- Descriptive analysis
- Segment Analysis

### Business Benefit:
- To predict the chances of new customers to churn
- To see the trend of customers churn

### Expected Outcome:
- Find out how much customer churn rate is in each country
- Find out how big the customer churn rate is based on gender
- Knowing the activeness of the customer to the level of customer churn

## Business Understanding
- What is the percent customer churn rate in each country?
- How many customer churn rates based on gender?
- How many active and inactive customers have churn? 
 
## Data Understanding
- source data : bank customer churn dataset by kaggle.
https://www.kaggle.com/datasets/gauravtopre/bank-customer-churn-dataset/code
- the dataset has 12 columns and 10000 rows.
- Data Dictionary:
	1. Customer ID - Unique ID given to identify a particular customer.
	2. Credit Score - It is the score which determines the creditworthiness of a customer.
	3. Country - The country where customer lives.
	4. Gender - The Sex of customer.
	5. Age - The age of customer.
	6. Tenure - Number of years the customer has Bank Account in that Bank.
	7. Balance - Amount of money present in customer's bank.
	8. Products Number - Number of Products from that Bank.
	9. Credit Card - Does the customer own a credit card of that Bank.
	10. Active Member - Whether the customer is an active member of that Bank.
	11. Estimated Salary - Total Income of the Customer.
	12. Churn
		1 = if the client has left the bank during some period
		0 = if he/she has not left the bank


## Data Preparation
- Code Used
- Python version:3.10.6
- Packages: Pandas, Numpy, Seaborn, Matplotlib, tqdm 

## Data Cleansing
- There are no missing values or duplicate data
- For data `credit_score`, `age`, `estimated_salary` have a mean value and 50% data have close values meaning this data has a good distribution
- No abnormal values were found in this dataset

## Exploratory Data Analysis
- We can ignore outliers on products_number and churn
- There are outliers in credit_score and age, for outliers we will leave them because they do not provide a significant value to the modeling
- For credit_score and age, the distribution is quite good, for balance outside the value of 0 the distribution is quite good, while for estimated_salary it has a comprehensive distribution on the data
- Female customers have a higher churn percentage than Male customers
- Customers in germany have the highest churn rate while the lowest are customers in france
- Based on the age of customers in the age of 40-60 years, the highest churn is
- Customers with low credit_score have the most chance of churn

## Modeling Data
- In this modeling, I transform categorical data into numeric data, while the method I take is to change `gender` and `country` with the OneHot Encoding method because the categorization data is still relatively small.
- After that I did Spitting the dataset with a comparison of data_train 70% and data_test 30%
- I classify this dataset as follows
	True Positive : He Left the Bank and is predicted to Left the Bank
	True Negative : He Hasn't Left the Bank and is predicted to Haven't Left the Bank
	False Positive : He left the bank and is predicted to Haven't Left the Bank
	False Negative : He Hasn't Left the Bank and is predicted to Left the Bank
- There are 4 models that I use, namely K-Nearest Neighbor, Logistic Regression, Decision Tree and Random Forest using a combination of oversampling and undersampling by looking at different coefficients

## Recommendation
- Of the 4 models made obtained:
- The highest f1 score value using the Random Forest model with a combination of oversampling and undersampling, with oversampling coefficients of 0.4 and undersampling of 0.7
- The highest Precision value using the Random Forest model with a combination of Oversampling and Undersampling, with oversampling coefficients of 0.3 and undersampling of 0.3
- The highest recall value using the Random Forest model with a combination of oversampling and undersampling, with oversampling coefficients of 0.3 and undersampling of 0.1
