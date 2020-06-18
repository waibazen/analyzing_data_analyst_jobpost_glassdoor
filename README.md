
# Data analyst Salary Estimator: Project Overview
Created a model that estimates data analyst salaries (MAE ~ $ 17K) to help data analysts negotiate their payscale when they offer a job
Scraped over 800 job descriptions from glassdoor using python and selenium
Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model.

Code and Resources Used
Python Version: 3.7
Packages: pandas, numpy, sklearn, matplotlib, seaborn, selenium

Scraper Github: https://github.com/arapfaik/scraping-glassdoor-selenium
Scraper Article: https://towardsdatascience.com/selenium-tutorial-scraping-glassdoor-com-in-10-minutes-3d0915c6d905


YouTube Project Walk-Through
https://www.youtube.com/playlist?list=PL2zq7klxX5ASFejJj80ob9ZAnBHdz5O1t

## Data Collection via Web Scraping:
Tweaked the web scraper github repo (above) to scrape 800 job postings from glassdoor.com. With each job, we got the following:

Job title
Salary Estimate
Job Description
Rating
Company
Location
Company Headquarters
Company Size
Company Founded Date
Type of Ownership
Industry
Sector
Revenue
Competitors
Data Cleaning

After scraping the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

<li>Parsed numeric data out of salary</li>
<li>Removed rows without salary</li>
<li>Parsed rating out of company text</li>
<li>Made a new column for company state</li>
<li>Added a column for if the job was at the company’s headquarters</li>
<li>Transformed founded date into age of company</li>
<li>Made columns for if different skills were listed in the job description:Python,R,Excel,AWS,Spark,ML</li>
<li>Column for simplified job title and Seniority</li>
<li>Column for description length</li>
<li>Column for num of competitors</li>

## EDA

I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables.

![alt text](https://github.com/waibazen/analyzing_data_analyst_jobpost_glassdoor/blob/master/eda.png "Logo Title Text 1")


## Model Building
First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

I tried three different models:

Multiple Linear Regression – Baseline for the model
Lasso Regression – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
Random Forest – Again, with the sparsity associated with the data, I thought that this would be a good fit.

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets.

<li>Random Forest : MAE = 19.05</li>

<li>Ridge (lasso)Regression: MAE = 17.63</li>
