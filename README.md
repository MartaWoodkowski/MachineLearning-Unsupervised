# Unsupervised Machine Learning - Cryptocurrency Clusters


* I was on the Advisory Services Team of a financial consultancy. One of the clients, a prominent investment bank, was interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, was lost in the vast universe of cryptocurrencies. They’ve asked me to create a report that includes what cryptocurrencies were on the trading market and determine whether they could be grouped to create a classification system for this new investment.

* I have been handed raw data, so I first needed to process it to fit the machine learning models. Since there was no known classification system, I needed to use unsupervised learning. I used several clustering algorithms to explore whether the cryptocurrencies can be grouped together with other similar cryptocurrencies. I put together a data visualization to show my findings with the investment bank.
### Data Preparation

* Read `crypto_data.csv` into Pandas. The dataset was obtained from [CryptoCompare](https://min-api.cryptocompare.com/data/all/coinlist).

* Discarded all cryptocurrencies that were not being traded. In other words, filtered for currencies that were currently being traded. Once I have done this, I dropped the `IsTrading` column from the DataFrame.

* Removed all rows that have at least one null value.

* Filtered for cryptocurrencies that have been mined. That was, the total coins mined should be greater than zero.

* In order for my dataset to be comprehensible to a machine learning algorithm, its data should be numeric. Since the coin names did not contribute to the analysis of the data, I deleted the `CoinName` from the original DataFrame.

* My next step in data preparation was to convert the remaining features with text values, `Algorithm` and `ProofType`, into numerical data. To accomplish this task, I used Pandas to create dummy variables. Then examined the number of rows and columns of my dataset. How did they change? Read my thoughts in [Cryptocurrencies workbook](unsupervisedML_crypto.ipynb).

* Standardized my dataset so that columns that contain larger values would not unduly influence the outcome.

### Dimensionality Reduction

* Creating dummy variables above dramatically increased the number of features in my dataset. I performed dimensionality reduction with PCA. Rather than specify the number of principal components when I instantiate the PCA model, it was possible to state the desired **explained variance**. For example, say that a dataset has 100 features. Using `PCA(n_components=0.99)` creates a model that will preserve approximately 99% of the explained variance, whether that means reducing the dataset to 80 principal components or 3. For this project, preserve 90% of the explained variance in dimensionality reduction. How did the number of the features change? Read my thoughts in [Cryptocurrencies workbook](unsupervisedML_crypto.ipynb).

* Further I reduced the dataset dimensions with t-SNE and visually inspect the results. In order to accomplish this task, I ran t-SNE on the principal components: the output of the PCA transformation. Then created a scatter plot of the t-SNE output. Observed whether there are distinct clusters or not.

### Cluster Analysis with k-Means

* Created an elbow plot to identify the best number of clusters. Used a for-loop to determine the inertia for each `k` between 1 through 10. Determined where the elbow of the plot was, and at which value of `k` it appeared.

### My Recommendation

* Based on my findings, made a brief recommendation to my clients. Can the cryptocurrencies be clustered together? Into how many clusters? Read my thoughts in [Cryptocurrencies workbook](unsupervisedML_crypto.ipynb).

## References

Crypto Coin Comparison Ltd. (2020) Coin market capitalization lists of crypto currencies and prices. Retrieved from [https://www.cryptocompare.com/coins/list/all/USD/1](https://www.cryptocompare.com/coins/list/all/USD/1)
