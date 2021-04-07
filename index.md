## Introduction

Pairs trading is an algorithmic trading strategy where we trade based upon the idea that a pair of securities will always revert back to their historical spread. In terms of making profit, we go long and short during the time period when the spread between these two stocks is abnormal. When the spread returns to its historical mean, we have made profit on one, if not both, of the positions. When trying to find which pair of stocks to use, looking at pairs of stocks in the same industry is the best idea because they will react to similar market factors and therefore, have similar price variations. Once investors believe to have found a pair of stocks, they will verify the prices of the two stocks are cointegrated before they plan on trading them. Finally, with the cointegrated pair of stocks, investors can begin trading utilizing different statistical thresholds that will allow them to figure out if the current spread is near the historical mean spread or not.

## Problem Statement

Given previous stock market data, we aim to employ Machine Learning to find the ideal pair of stocks and predict their future spread which we can trade upon. Predictive models in the stock market are mainly used to learn about the upcoming activity and fluctuation of different securities. Attaining a precise and faultless projection leads to a potential increase in excess return (or alpha) for financial institutions and investors. Machine Learning is useful in this context because there’s a large range of ML methods that have the possibility of discovering intuitions and patterns on a set of data, leading to important resolutions.

## Methods

Chronologically, our first ML method OPTICS, is an unsupervised method similar to DBSCAN that will result in unique clusters of high density. This method will allow us to take a large random pool of stocks and cluster them based on their correlation. We picked OPTICS over DBSCAN because it can handle clusters of varying density. Then, we will conduct the Augmented Dickey Fuller Test (ADF) to find the cointegration between each stock in a cluster which will allow us to determine ideal pairs within each cluster. Finally, we will use the LASSO regularized regression method to predict the future spread between an ideal pair which can be used to determine the z-score to trade on.

## Results

Ideal results will provide information regarding which correlated stocks are diverging in order to identify which stock should be opened on the long position and which should be opened on the short position. Our analysis is based on the assumption that the spread of a pair of correlated stocks will eventually converge.  

In order to implement the ridge regression model, we chose two stocks that are known to be highly correlated: Ford and GM. Using those, we trained our Ridge regression using 4/5 of the prices of these stocks. Using these weights, we fit our model onto the testing data and plotted our results. These are shown on the figure below. 

![image](https://user-images.githubusercontent.com/51150161/113919797-ffb52800-97b1-11eb-81cc-bdaed350c767.png)

![image](https://user-images.githubusercontent.com/51150161/113919463-a3520880-97b1-11eb-9243-563ab123b15d.png)

Our results are not ideal because the model only has one weight, so the regression shows a straight line as opposed to a polynomial fit. This does not accurately represent the spread between the stocks. In order to fix this, we will train the model with more features in order to generate a polynomial fit. Additionally, to find the spread between the data, we will define a spread function which will give us information about which stocks are converging and diverging. 


Our lasso regression implementation was similar to our ridge. We used the same GM and Ford stocks and trained our model using 4/5 of the prices of the stocks. We obtained a fit from the data, but ran into the same issues as we did with Ridge regression. We will make the same modifications that we will make for the Ridge regression. 


## Discussion

By utilizing a combination of ML methods and algorithms, individual investors and small-time traders no longer have to rely on the sole method of regression to aid in pair selection, and will eventually achieve a higher return on their investment. Our model should be able to simulate mean-reverting stock pairs and differentiate them from those who have a correlation but their spread is non-stationary. Meaning, ML can help identify stocks that do not belong to the same industry nor have similar characteristics but do have a correlation, increasing the possibility of making a profit. 

Additionally, it will be interesting to explore the impact of selecting distinct thresholds to signal a diverging spread between identified stocks. Selecting appropriate benchmarks for spread divergence may help reduce market-risk exposure, helping small-time investors achieve a consistent return regardless of the direction of the market. 

## References

Sarmento, S., & Horta, N. (2020, May 04). Enhancing a pairs trading strategy with the application of machine learning. Retrieved March 03, 2021, from https://www.sciencedirect.com/science/article/pii/S0957417420303146 

Vidyamurthy, G. (2011). Pairs Trading: Quantitative Methods and Analysis. Hoboken: John Wiley & Sons. 

Chien-Feng Huang, Chi-Jen Hsu, Chi-Chung Chen, Bao Rong Chang, Chen-An Li, "An Intelligent Model for Pairs Trading Using Genetic Algorithms", Computational Intelligence and Neuroscience, vol. 2015, Article ID 939606, 10 pages, 2015. https://doi.org/10.1155/2015/939606 
