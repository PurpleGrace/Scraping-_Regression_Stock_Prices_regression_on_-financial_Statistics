## Web Scraping and Linear Regression Project
Identify relationship between stock prices and financial statistics
Abstract
The goal of this project is to  find out how much a public company’s stock price can be explained by its financial numbers. The project uses a few financials as features and stock closed price on Oct 4th as dependent variable. The algorithm used includes Ordinary least square regression, regulations like Lasso, Ridge, and ElasticNet. I also use a dummy variable to improve the model. The research will help potential investors, traders, and whoever insisted to make better informed decisions based on the contents the project offers.
Design
The data used in the project are web-scraped from website https://finance.yahoo.com and https://stockanalysis.com/stocks/  Financial information provided in “Summary” and “Statistics” section will be collected. After data cleaning and wrangling, I did OLS linear regression model, checked assumptions and evaluation. Lasso, Ridge and ElasticNet regression model with cross validation are also performed to seek a better model with less variances. The project later uses a categorical variable “Industry” as dummy variable to make improvement.
Data
I scrape ticker list info from https://stockanalysis.com/stocks/ and for each ticker go to https://finance.yahoo.com to collect “Summary” and “Statistics” data. Total 5000 company tickers tried, but after cleaning and wrangling, only 1453 company data points are reliable and used. “Previous Close” is the company’s stock price closed on Oct 4th, total 34 features are collected.
Tools
request, selenium for data web scraping ;
BeautifulSoup for HTML syntax parsing ;
pandas and numpy for data manipulation ;
Matplotlit and Seaborn for data visualization;
Pickle for data object serialization and de-serialization
sklearn and statsmodels for regression


Algorithms
Clean data: check/transfer data types, deal with missing value. 
Create a baseline OLS linear regression model on all features. 
Check assumptions and evaluation: get rid of outliers, check VIF and move away features of collinearity, transform dependent feature with log function to correct non_normality. 
Compare R squared values for regressions with / without historical price feature

Add Polynomial features and try different regulation methods with cross validation: Lasso, Ridge and ElasticNet, and choose the model with best mean R squared value.

Add available dummy variable “Industry” to improve model.
