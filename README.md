Overview
========

-  Implementing PCA using Rapid's CuML and S&P 500 Index stock data
We look will look at model-free factor analysis using PCA. By model-free we mean that we do not rely on any factors such as value or momentum to decompose portfolio returns, but instead using Principal Component Analysis (PCA) to deduce structure of portfolio returns.

- Part 1 (Asset Returns Calculation)
Before we start building the PCA model with the dataset, we want to account for stationarity in stock prices. To address this problem, we calculate for percent returns, also known as simple returns using asset_prices. We will assign the result to variable asset_returns.
We now compute stock returns and normalize stock returns data by subtracting the mean and dividing by standard diviation. This normalization is necessary for PCA to perform well. This is because PCA calculates a new projection on the data set, and the new axis are based on the standard deviation of the variables. Thus, a variable with a high standard deviation will have a higher weight for the calculation of axis than a variable with a low standard deviation. When we normalize the data, all variables have the same standard deviation, thus all variables have the same weight and the PCA calculates relevant axis in relation to others

- Part 2 (Eigen-portfolios construction) Following Avellaneda we define eigen portfolio weights as:
Q(j)i=v(j)iσi where  j  is the index of eigen portfolio and  vi  is the i-th element of j-th eigen vector. In the code the pca.components_ are the Principal axes in feature space, representing the directions of maximum variance in the data. The components are sorted by explained_variance_. We then normalize the portfolio weights so they sum up to one, where positive means a long position and negative value means a short. The weights of the first eigen portfolio will be pc_w

- Part 3 (Evaluating the performance of eigen portfolios using sharpe ratio)
In the part, we shall backtest our eigenweighted portfolio with our out-of-sample testing dataset. An appropriate evaluation metric will be chosen, in this case sharpe ratio, and compared with the other eigen portfolios. The portfolio with the highest sharpe ratio will be chosen as the final model for our PCA strategy


Making the bridge to the financial markets, by obtaining the principal components
of a data set composed by a time series of stock returns, each principal component can be
seen as representing a risk factor. The first component, which accounts for most of the
variation of the data, is widely accepted as representing the market returns, while
companies with similar coefficients related to the second component tend to be from the
same industry (Avellaneda e Jeong-Hyun 2010). 

