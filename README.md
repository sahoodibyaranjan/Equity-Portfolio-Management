# Equity-Portfolio-Management

Data Preparation
Download the historial daily data of the entire 2018 for the 10 stocks
universe = ['IBM', 'MSFT', 'GOOG', 'AAPL', 'AMZN', 'FB', 'NFLX', 'TSLA', 'ORCL', 'SAP']
For example, to download IBM data, use the following link to go to yahoo finance page. Find the "Download Data" link to download the csv file to you local disk. https://finance.yahoo.com/quote/IBM/history?period1=1514782800&period2=1546232400&interval=1d&filter=history&frequency=1d
Replace "IBM" with other stock symbol in the above URL, you will be able to download data for other 9 stocks.
You should have 10 csv files on your disk now. IBM.csv, MSFT.csv, etc. We call the 10 stocks "universe" which is the entire stock market you can trade.
image.png
Retrieve the "Close" and "Adj Close" values for each stock
You will create a dataframe where there are 20 columns for the 10 stocks, each row is the "Close" and "Adj Close" prices for the 10 stocks on each day, in the order of the business days in 2018. Assume all buy/sell on the "Close" prices and there is no transaction cost.
You start to manage 5 million dollars fund on Jan 02, 2018
You have a strategy to manage the fund.
On Jan 02 2018, you split the $5m into 5 $1m, and use them to buy 5 stocks from the 10 stocks. For example, IBM close price was  154.25.𝑊𝑖𝑡ℎ 1m, you can buy max 6482 shares with cost  999848.5𝑤𝑖𝑡ℎ 151.5‬ cash left. You decided to spend  1𝑚𝑜𝑛𝑒𝑎𝑐ℎ𝑜𝑓[′𝐼𝐵𝑀′,′𝑀𝑆𝐹𝑇′,′𝐺𝑂𝑂𝐺′,′𝐴𝐴𝑃𝐿′,′𝐴𝑀𝑍𝑁′]𝑟𝑒𝑠𝑝𝑒𝑐𝑡𝑖𝑣𝑒𝑙𝑦𝑎𝑛𝑑𝑘𝑒𝑒𝑝𝑡ℎ𝑒𝑟𝑒𝑠𝑡𝑐𝑎𝑠ℎ𝑖𝑛𝑡𝑜𝑎𝑧𝑒𝑟𝑜−𝑖𝑛𝑡𝑒𝑟𝑒𝑠𝑡𝑐𝑎𝑠ℎ𝑎𝑐𝑐𝑜𝑢𝑛𝑡.𝑂𝑛𝐽𝑎𝑛022018,𝑦𝑜𝑢𝑟𝑚𝑎𝑟𝑘𝑡𝑜𝑚𝑎𝑟𝑘𝑒𝑡𝑣𝑎𝑙𝑢𝑒(𝑀𝑇𝑀)𝑖𝑠 5m if combining all stocks value and cash. Your holdings of stocks and cach account is your portfolio.
 𝑀𝑇𝑀𝑡=𝑐𝑎𝑠ℎ𝑡+∑𝑘=15𝑆ℎ𝑎𝑟𝑒𝑠𝑡𝑘×𝐶𝑙𝑜𝑠𝑒𝑃𝑟𝑖𝑐𝑒𝑡𝑘  
Your trading strategy is "5 days rebalancing of buying low". Here is how it works. You keep your portfolio unchanged until 5 days later on Jan 09 2018. Now you want to re-check the market and adjust your portfolio. You will compute the "Adj Close" price changes from Jan 02 to Jan 09, and find the 5 stocks whose "Adj Close" prices dropped the most in terms of percentage. You sell all current holdings on Jan 09 "Close" prices to convert your portfolio to all cash. Then immediately split your cash, including your cash account, to 5 equal parts to buy the 5 stocks that dropped the most from Jan 02 to Jan 09 on 'Adj Close' prices. You always buy the max shares of stock on the "Close" price and keep the rest cash in cash account. Now the portfolio should be different from 5 days ago. This operation is called "rebalancing".
Keep in mind, the MTM will change every day, even when your portfolio holdings don't change, because the stock prices change.
Corporations generally issue stock dividends on some days. The total dividend you get on such a day is the stock dividend times your shares if you have shares of this stock on the dividend day. If you buy shares on the dividend day, these bought shares are not qualified to get dividend. If you sell shares on the dividend day, the sold shares are qualified to get dividend. For example, on 2/8/2018, IBM issued $1.5 dividend per share. In your cash account, you will automatically get
$1.5×(𝑦𝑜𝑢𝑟 𝐼𝐵𝑀 𝑠ℎ𝑎𝑟𝑒𝑠 𝑜𝑛 2/8/2018) 
5 business days later on Jan 17 (Jan 15 was a holiday), you re-check the market and adjust your portfolio again. You will have a new portfolio on Jan 17.
If you run this strategy every 5 days all the way to Dec 31 2018, you will have a daily MTM. You expect the MTM on Dec 31 2018 should be higher than $5m because you always buy the stocks that dropped the most, i.e., you always buy low.
Another strategy is "5 days rebalancing of buying high". You always buy the 5 stocks whose "Adj Close" prices surge the most in terms of percentage because you believe the trend will continue. Run the new strategy and see how the MTM will change.
You will create a "high tech index" which is simply the daily average of the 10 stocks "Close" prices. Compare your MTM series with the "high tech index" and plot their curves. To plot the two curves together, you may want to convert the series to daily percentage change with regard to Jan 02 2018.
Download the USD/JPY 2018 historical data at https://www.myfxbook.com/en/forex-market/currencies/USDJPY-historical-data then use the "Close" column as the rate to convert your MTM series from USD to JPY. Plot the two MTM curves. You will need to convert to daily percentage change too.
The above two strategies both rebalance every 5 days. Try to change the days interval and find the optimal days interval that maximizes the MTM on 12/31/2018.
