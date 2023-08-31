# Features

In the first stage, we focus on the trade price change of stocks ( $k$ th $\in \{1,2,.., K\}$) during a time period, $t_i$, $i \in {1,2,..., n}$.  Let's denote the price for the $k$ th stock at time $t$ as $X(t)$. 

We hope to find features to represent the information on price change in the time period. 

There are two main parts of information we could consider: 

* Tendency, whether the price is going up or down overall. 
* Variability, whether the price changes a lot during the period. If there is low variability, the price trend is more clear than the scenario when there is high variability.

Also, note that we have $K$ different stocks with different price ranges. We need to account for this difference.  

## Potential Ideas 

### Simple summary statistics 

We could just set a sample scare value to represent the feature: 

* Open price $X(t_1)$
* Close price $X(t_n)$
* High price $\max(X(t))$
* Low price $\min(X(t))$

Those features only utilize one of the $n$ points and will lose information. (those can be the baseline features. the new features should have higher correlation with the target than those baseline)

We could also consider the price change rate to incorporate the price range difference: 

* Simple price change rate: $\frac{X(t_n) - X(t_1)}{X(t_1)}$
* Mean price change rate: $$\sum_{i=1}^{n-1} \frac{X(t_{i+1}) - X(t_i)}{X(t_i)}$$
* Weighted mean price change rate: $$\sum_{i=1}^{n-1} w(t_i)\frac{X(t_{i+1}) - X(t_i)}{X(t_i)}$$ where $w(t_i)$ is a weight function with $\int w(t) = 1$ in the time period and we should put more weight at the end of the period.

### Regression 

Fit a linear regression $X = \beta_0 + \beta_1 t$ and use 

* $\beta_1$ to represent the overall trend.
* $R^2$ to represent the variability.

Since there is an issue with the price range, the feature can be represented as 
$$\frac{\hat \beta_1}{X(t_n) - \hat \beta_0} \times R^2$$


### Time series analysis 

### Functional data analysis 

Functional PCA

### Wavelet analysis 

count change frequency

### Smooth consideration 

Gaussian kernel 




# Exploration 

1. run the sample statistics to get the boundary of correlations
2. run slope method
3. run return, weighted return
4. wavelet analysis
5. time series kmeans, functional pca





