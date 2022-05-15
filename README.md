
# Sales Regression Analysis

Regression analysis of sales data from two different datasets.

## About

Linear regression and logistic regression have been applied on dataset where one represents sales data and other represents if the consumer has subscribed to term deposit.

The sales data consists of n number of integers which are not categorical. So linear regression is applied to find the effect of independent variable over dependent variable.

In another dataset the dependent variable is in categorical form, so applied logistic regression in it.

R lauguage is used as we just need to define a function in a pipline. Therefore, tasks become more earier.

## Data Pipeline in R

```r
  data_clean = df %>%
    drop_na() %>%
    janitor::clean_names()
```

## About Dataset

 - The first dataset is the advertising dataset which consists of sales through tv, radio and newspaper.

 - The second dataset is related with direct marketing campaigns of a Portuguese banking institution. The marketing campaigns were based on phone calls. Often, more than one contact to the same client was required, in order to access if the product (bank term deposit) would be ('yes') or ('no') subscribed.

## Data Cleaning

In first dataset, 
 - x parameter has been removed as it will not be used.

```r
  data_clean = df %>%
    subset(select = -c(x))
```

In second dataset, 
 - columns are renamed for better understanding. 

```r
  colnames(data_clean) = c("age",
                        "job",
                        "marital",
                        "education",
                        "credit_default",
                        "balance",
                        "house_loan",
                        "personal_loan",
                        "contact",
                        "days",
                        "month",
                        "duration",
                        "campaign",
                        "pdays",
                        "previous",
                        "poutcome",
                        "term_deposit")
```
 - Dependent variable has been renamed from yes-no to 1-0. 

```r
  data_clean$term_deposit[data_clean$term_deposit == "yes"] = 1
  data_clean$term_deposit[data_clean$term_deposit == "no"] = 0
```

 - Data types are converted to numeric.

```r
  data_clean$term_deposit = as.numeric(data_clean$term_deposit)
```

## Linear Regression

Linear regression analysis is used to predict the value of a variable based on the value of another variable. The variable you want to predict is called the dependent variable. The variable you are using to predict the other variable's value is called the independent variable.

On first dataset, linear regression is applied where sales was the dependent variable and all other parameters are dependent variable. As it is a linear model, so independent variable is used one at a time.

#### Case 1

TV is used as a independent variable and sales is used a dependent variable.

![tv_sales](results/tv_sales.png)

The above result shows that as the tv watch increases, sales increases.

 - Multiple R-squared: 0.6119
 - Adjusted R-squared: 0.6099 
 - p-value < 2.2e-16 

As p-value is very close to 0, therefore, highly significant that result doesn't happened by luck.

#### Case 2

Radio is used as a independent variable and sales is used a dependent variable.

![radio_sales](results/radio_sales.png)

The above result shows that as the radio listening increases, sales increases.

 - Multiple R-squared: 0.332
 - Adjusted R-squared: 0.3287 
 - p-value < 2.2e-16 

As p-value is very close to 0, therefore, means highly significant that result doesn't happened by luck.

#### Case 3

Newspaper is used as a independent variable and sales is used a dependent variable.

![newspaper_sales](results/newspaper_sales.png)

The above result shows that as the newspaper reading increases, sales increases.

 - Multiple R-squared: 0.05212
 - Adjusted R-squared: 0.04733 
 - p-value = 0.001148 

As p-value is very close to 0, therefore, means highly significant that result doesn't happened by luck but still more than the previous two cases.

## Logistic Regression

Logistic regression is a process of modeling the probability of a discrete outcome given an input variable. The most common logistic regression models a binary outcome; something that can take two values such as true/false, yes/no, and so on.

To perform logistic regression task, second dataset has been used. Multiple csv files were given form which bank-full.csv has been used.

For now, two variable that are balance and campaign were used as an independent variable and term_deposit as independent variable.

![logistic_regression](results/log_reg.png)

Accuracy = 0.881931 or 88.19%

## Support

For support, find me 😂.

## Authors

## Acknowledgements



