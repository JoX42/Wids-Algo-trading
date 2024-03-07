Algorithmic Trading using ML

Momentum Trading - An Introduction

The usual philosophy of trading in the stock market is: buy when low, sell when high. Momentum trading strategy is however, different. Momentum, in the world of trading, is defined as the rate of change of returns of a stock or an index. This rate can be calculated on a daily, weekly, monthly or even a yearly basis.

It aims to buy the securities that show a good upward price trend. If a trend is established, the ‘market force’ will continue to drive the security in that direction.

Points to note:
In a ML trading model, careful feature selection is important, or the model will overfit by correlating the wrong features and make poor predictions on unseen data, giving -ve PnL values.
In general, the predictive power of a trading model should come mainly from its features, not from the ML algorithm being used.
One should also take care of data-mining bias. When the model correlates the wrong changes with market price trends, it leads to data-mining bias. It assumes that an important event happened due to which market prices greatly fluctuated (or a big market change occurred); whereas the reality is that the price changes occurred just by chance and not because of that event.
Another important feature of time-series data is - regimes. Regimes refer to the tendency of financial markets to change their trend abruptly. So it may occur that a trained model performs well on its training price data, but very poorly on test data, because the test set may be from a different regime.

Once a trading model is prepared, a backtesting library (e.g. Auquan) can be used to check how well the trading model performs.




Creating a momentum portfolio:

1) Creating a stock universe

Analysing and tracking the returns of all the stocks listed on the stock market will be tedious. Hence, we create a tracking universe. We analyse the stocks in our tracking universe and then create our portfolio. For example, a simple tracking universe can be BSE500 or Nifty50.

It is recommended to have around 150-200 stocks in the tracking universe to build a portfolio of around 12-15 stocks.

2) Collecting and setting up data

Collect the opening and closing prices of all the stocks in your universe across a timeline.

3) Calculate Returns

Compute the returns for all the stocks in the universe and rank them accordingly. This return can be calculated on a daily, weekly, monthly or yearly basis. The best performing stock, i.e. the one with the highest return would be ranked first.

4) Creating a portfolio

We select the top 10-15 stocks from the ranked list of stocks in our portfolio. This, however, does not mean that the remaining stocks are discarded; they will continue to be a part of the tracking universe.

If a stock has a high rate of returns, it possesses good momentum. The buyers in the market, on noticing the rising stock price, will be tempted to buy it. This would result in further increase of the price. The price of the stock, therefore, will continue to rise until something happens in the market which forces the stockholders to sell their stock. 

Momentum strategy generally doesn't include the low return stocks. It includes those stocks which have a high price but are expected to show further increase in price, unlike the orthodox strategy of buying under-priced stocks and waiting for them to rise.

Traders use both long and short strategies for trading using the momentum strategy.

5) Carry out the same analysis monthly

Once the portfolio has been created and bought, we carry out the same process again after a month, using the latest 12 month data. Using the new rankings, we make changes to our portfolio.


Momentum Strategy Indicators:

1) Trendlines

Catch the general trends for the stock. Generally, the stock prices vary quite frequently, which results in the Price Vs. Time curve to have many spikes. To estimate if the stock price is showing an upward or a downward trend in the long run, trendlines are used. 

2) Moving Averages

Again, to get a general trend of the stock price, moving averages indicator is used. This indicator continuously calculates the average value of price as new data is fetched, which nullifies the spikes in the graph and gives a comparatively smoother curve.

3) Stochastic Indicator

Stochastic indicator is a leading indicator predicting the change in direction of momentum. This is used to time entry and exit points. The Stochastic Indicator has a range from 0 to 100. When the value approaches 100, it indicates that the stock is overbought. Similarly, as it approaches 0, it indicates that the stock is oversold. However, this is not very accurate.

4) Average Directional Index

This shows the strength of a trend but not the direction. Low value of the indicator indicates a stagnant and directionless market. The higher the reading, the stronger the trend. This is generally used with other indicators to get the direction of momentum.




Hurst exponent:
It is another measure of the long-term memory of a time-series data. It is generally a good indicator to find trends. A Hurst exponent greater than 0.5 indicates that a clear trend exists, and the greater the value, the better the trend. On the other hand, Hurst exponent < 0.5 indicates mean-reverting behaviour, which means that the prices do not show any steady rise or fall, but keep converging to their mean value periodically.



Application in this Project:

Applying the above ideas in the project using pandas and yfinance libraries

Momentum trading is all about going short or long at the appropriate opportunity. 

A market is called bullish when it is going upward and we go for long this time.

Similarly a market is bearish when it is going downward and we tend to short. Overbought conditions lead to bearish reversal.

Another important point is identifying entry and exit points which is done by candlestick and chart patterns

Entry Rule:

When the closing price is less than daily average price.

Exit Rule:

Stop loss
Profit exit

Traders employ stop-loss orders as a form of order to control their losses or lock in profits on open positions. By putting down a stop-loss order, traders can limit their exposure to risk.

Stop-losses are always set higher than the going rate for a buy or lower than the going rate for a sale.

Once the stop price is met, the stop order becomes a market order and is executed at the next available opportunity.


Stop loss may be static or dynamic. Static being a fixed number with respect to the starting position of the stock while the dynamic changes as a certain percentage of the current market price.

Take-profit, or limit orders, are the same as stop-losses in that they are converted into market orders to close a position when a point is reached.However, The exit point must be for a profit. (Below market price for a short trade and above price for a long trade.)

Implementation:

In this project, firstly we have created a stock universe, by downloading and collecting the different tickers into a dataframe. 

Through this, we calculated the cumulative returns to get the overall return of a stock over the analysis period. We also calculated the monthly and yearly returns.

Using the 12-month analysis, we select the top-performers to make our portfolio. 

We use this portfolio to find the returns for the following month. The average return of this portfolio comes to be +3.53 %.

Next, we have put a momentum trading technique into practice and test it to determine if it has any chance of paying off. We are given access to a wide selection of stocks and time frames. In order to generate predicted returns, we then computed the signal for the specified time period and applied it to the dataset. In order to determine whether the signal has an alpha, we ultimately did a statistical test on the mean of the returns.

We have used Apple’s stock(AAPL) to carry our strategy.

A series of trading events, or outcomes, that can be utilised to trigger trading events, constitute a trading signal. Making a "long" and "short" portfolio of equities for each date is a typical format (e.g. end of each month, or whatever frequency you desire to trade at). This signal can be taken to mean that you should rebalance your portfolio on each of those days by taking the appropriate long ("buy") and short ("sell") positions.

Our null hypothesis: the mean return from the signal is 0. (Any p-value > 0.1 implies the null-hypothesis cannot be rejected.)



Strategy: 

For each month-end observation period, we ranked the stocks by previous returns, from the highest to the lowest. We select the top performing stocks for the long portfolio, and the bottom performing stocks for the short portfolio.


Result: 

The average return of this portfolio comes to be +3.53 %.


Result of our Hypothesis Testing:
Alpha level = 0.05 
T-test returned a p-value of 0.21

This is a very high p-value so we cannot reject the null hypothesis.

We therefore come to the conclusion from this t-test that our signal was not strong enough to give us positive returns. In other words, our signal is not profitable.


Conclusion:

We conclude that the average return of our portfolio came to be positive.  


  
