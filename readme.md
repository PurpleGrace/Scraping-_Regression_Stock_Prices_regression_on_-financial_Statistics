## Identify relationship between stock prices and financial statistics
### Abstract
The goal of this project is to  find out how much a public company’s stock price can be explained by its financial numbers. The project uses a few financials as features and stock closed price on Oct 4th as dependent variable. The algorithm used includes Ordinary least square regression, regulations like Lasso, Ridge, and ElasticNet. I also use a dummy variable to improve the model. The research will help potential investors, traders, and whoever insisted to make better informed decisions based on the contents the project offers.
### Design
The data used in the project are web-scraped from website [yahoo](https://finance.yahoo.com ) and [stockanalysis](https://stockanalysis.com/stocks/)  Financial information provided in “Summary” and “Statistics” section will be collected. After data cleaning and wrangling, I did OLS linear regression model, checked assumptions and evaluation. Lasso, Ridge and ElasticNet regression model with cross validation are also performed to seek a better model with less variances. The project later uses a categorical variable “Industry” as dummy variable to make improvement.
### Data
I scraped ticker list info from [stockanalysis](https://stockanalysis.com/stocks/) and for each go to [yahoo](https://finance.yahoo.com )to collect “Summary” and “Statistics” data. Total 5000 company tickers tried, but after cleaning and wrangling, only 1453 company data points are reliable and used. “Previous Close” is the company’s stock price closed on Oct 4th, total 34 features are collected.
### Tools
- request, selenium for data web scraping ;
- BeautifulSoup for HTML syntax parsing ;
- pandas and numpy for data manipulation ;
- Matplotlit and Seaborn for data visualization;
- Pickle for data object serialization and de-serialization
- sklearn and statsmodels for regression


### Algorithms
1. Clean data: check/transfer data types, deal with missing value. 
2. Create a baseline OLS linear regression model on all features. 
3. Check assumptions and evaluation: get rid of outliers, check VIF and move away features of collinearity, transform dependent feature with log function to correct non_normality. 
4. Compare R squared values for regressions with / without historical price feature
5. Add Polynomial features and try different regulation methods with cross validation: Lasso, Ridge and ElasticNet, and choose the model with best mean R squared value.
6. Add available dummy variable “Industry” to improve model.

### Result

#### 1. Linear regression with historical price feature: “52 Week High 3”:

The R-squared and Adj. R-sqaured are both terrifically high, it is caused by feature “52 Week High 3”. “52 Week High 3” is defined the highest price at which a security, such as a stock, has traded during previous 52 weeks. It is an important factor in the analysis of a stock's current value, so it is very reasonable to have a high R squared value with “52 Week High 3” as one of our feature.

#### 2. Linear regression without historical price related feature.
Generally speaking, the financial numbers of a public company explains 56.5% of its stock price.

#### 3. Regression with Regulations:
Among all the models I have trained with cross validation, including  Lasso, Ridge and ElasticNet, ElasticNet performed best with best mean R^2 of 0.531.

##### Insight:
- 'Revenue Per Share (ttm)', 'Diluted EPS (ttm)', '52-Week Change 3', '% Held by Institutions 1', 'Profit Margin', 'Payout Ratio 4', 'Return on Assets (ttm)', 'Return on Equity (ttm)''Total Debt (mrq)’ have a Positive relationship with stock price. For example: For every dollar increase in Diluted EPS, the stock price will increase e^(0.229) = 1.26 times
- ‘Avg Vol (10 day) 3', 'Shares Short (prior month Aug 13, 2021) 4’ have negative relationship with stock price. For example, for every share Short by investors, the stock price decrease by (1-np.e**-0.049132) = 4%

#### 4. What if feed all non-price-related features to ElasticNet model
The mean score increased slightly, but our model will become much more complex.

#### 5. linear regression with dummy variables “Industry"
The R squared value will increase to 0.601, but model will become more complex.
