# Meme Stock Analysis
## _Hype or an Opportunity?_

After the 2020 pandemic induced ride in the stock market, 2021 opened with it's own surprises.

Two stocks, GameStop (NYSE:GME) and AMC Theatres (NYSE:AMC) were viewed by Wall Street
professionals as stocks on the way down. 

![GME logo](PNG/GME.png "GME logo")

GameStop (GME) is a company that sells video games and surrounding products. 
With video gamers increasingly downloading games directly, GameStop seemed poised 
to suffer a similar fate as Blockbuster Video and Borders Books. 

![AMC logo](PNG/AMC.png "AMC logo")

AMC Theatres(AMC) was hit hard by the pandemic shut downs. Movie theatres remained closed for over a year
with major studios holding back major releases until fans were ready to go back to the theatre, or the studios started releasing new films directly to their streaming services. The success of the streaming releases indicated that movie thetres may never return to the big crowds previously experienced.

Based on these fundamentals, many Wall Street firms, including large hedge funds, 
were shorting these two stocks. It appeared to be a safe bet.

The stock market rebound during the second half of 2020 was accompanied by the growth of several 
FinTech firms that were designed to make stock investing easier for new and/or small investors. 
With the markets rising and stimulus checks flowing, many new investors entered the market.

![Robinhood logo](PNG/Robinhoodlogo.png "Robinhood logo")

Many of these new investors joined other "Main Street not Wall Street" investors in on 
online forums such as Reddit, to gain knowledge and share investing tips. One of the more
popular forums, a SubReddit called ["wallstreetbets"](https://www.reddit.com/r/wallstreetbets/) started a movement to benefit retail investors at the expense of the large hedgefunds. It started a bull run on GME and AMC stocks. Borrowing from the phenomena of cryptocurrencies which were promoted by social media memes, Dogecoin being the best known, GME and AMC gained the moniker of ["Meme Stocks"](https://blog.mywallst.com/what-is-a-meme-stock/) or even ["Stonks"](https://www.thebalance.com/stonks-5118087).

By January 27, 2021, Robinhood and other trading platforms moved to limit buying and selling of GME and AMC.
The unprecedented action led to cries of unfairness to retail investors and eventual [Congressional hearings](https://www.nasdaq.com/articles/three-takeaways-from-congresss-gamestop-gme-hearing-2021-02-19).

We decided to analyze the following questions raised by the Meme Stock phenomena:

- Can Meme stocks stand up to a traditional financial analysis?
- Are Meme stock investors the same as crypto investors? Can this be proven by a negative correlation in their prices?
- Are Meme stock prices truly driven by forums such as wallstreetbets?
- Are Meme stocks a real money making opportunity?

## Financial Analysis

We downloaded the GME and AMC data from the Alpaca API from January 1st, 2021 through the end of May. We compared the close date data with the S&P 500 stock index (NYSE:SPY). Here's what we found:

![Meme Stock Daily Returns](PNG/meme_stock_plot.png "Daily Returns")

By this graph it looks like the meme stocks only perform well on certain dates but over all follow the S&P 500.

Then we calculated and graphed the cumulative returns:

![Meme Stock Cumulative Returns](PNG/cumulative_returns_plot.png "Cumulative Returns")

This showed that over the first five months of 2021, the cumulative returns of the meme stocks were clearly superior to the S&P 500.

We did a risk anlaysis comparison of the three:

![Meme Stock Risk](PNG/risk_plot.png "Risk")

Then we did calculated the standard deviation and the annualized standard deviation for the three tickers. Unsurprisingly, the both the standard deviation and annualzed standard deviations for GME and AMC were much higher than for the S&P 500:

**Standard Deviation**

AMC    5.223645

GME    4.102531

SPY    0.143349

**Annualized Standard Deviation**

AMC    5.223645

GME    4.102531

SPY    0.143349

Next we calculated the Shape Ratios. Sharpe Ratios are a standard way of assesing risk vs reward. Generally,
the higher the Sharpe Ratio the better. Above 2 is good and above 3 is excellent. Here is what we found:

**Sharpe Ratio**

AMC    2.351388

GME    3.286217

SPY    2.337867

![Meme Stock Sharpe Ratios](PNG/sharpe_ratios_plot.png "Sharpe Ratios")

Sharpe Ratios above 2 are good and above 3 are excellent. AMC is lightly better than S&P 500 while GME is excellent. 

We then performed a Monte Carlo simulation alaysis of a portfolio consisting of one third, GME, one third AMC and one third SPY (we included the S&P index as a hedge against any massive instability).

Using the first five months as our historical data we ran a one year projection through ten thousand simulations.

![Meme Stock Monte Carlo Sim](PNG/MC_Sim.PNG "10,000 Simulations")


We then assumed an initail investment amount of $1,000 (this seemed reasonable as many of the meme stock investors are smaller retail investors).

The results were impressive. 

There is a 95 percent chance that an initail investment of  $1000 in the portfolio over the next year will end within the range of $6,281.01 and $30,569,750.65. 

> These are results are based on five months of historic data.
> Most Monte Carlo Simulations rely upon years of historical data.
> We only used the first five months of 2021 for these simulations since
>we are examining the meme stick phenomena which just began this year. 

## Financial Analysis Conclusion

The meme stocks were able to stand up to a traditional financial analysis. The risk as indicated 
by the standard deviations and the Sharpe Ratio calcualtions is lower than might be expected for such volatile stocks. 
The potential upside is huge. 

## Crypto and Meme Correlation?

A perception that exists in online forums is that meme stock investors are just cryptocurrency, or even meme crypto investors that are pulling their money back and forth between the meme stocks and cryptos. We tried to determine if this is true.

We pulled crypto currency data from the CoinApi. As free API, CoinAPI limited us to 100 trading days worth of data. There are other free coin API's but their historical data does not go up to this year, when the meme stock phenomena began. We pulled data from January 1, 2021 through April 2021 for Bitcoin (BTC) and Dogecoin (DOGE).

We then calulated cumulative daily returns and merged this with our cumulative dailey returns for the meme stocks.
What we found was this:

![Meme vs Crypto Cumulative](PNG/Meme_vs_Crypto_cum.png "Meme Crypto Cumulative")

If the meme stock investors and the meme coin investors are rolling money back and forth between those investments, there should be a negative correlation shown between meme stocks and meme coins daily cumulative return. Except for a few short days at the beginning of April, this does not appear to occur. In fact, the large January surge in meme stocks is almost mirrored by large gains in Dogecoin. 

## Crypto Meme Correlation Conclusion

Based on the above graph, it appears that a back and forth between meme stock money and meme coin money is not occuring. 
It seems that perception is false.

## Meme stocks driven by forums?

The accepted narrative is that meme stock prices are driven by online forum discussions. We decided to look for a way to prove this was true with numbers.

We used the praw, the Python Reddit API Wrapper to extract top mentions of GME and AMC and variations of their names from the wallstreetbets subreddit. We then counted the number of mentions per day:

![WallStreetBets](PNG/wsb_mentions.PNG "Mentions")

We then combined that data with our daily cumulative returns data for the meme stocks. 


Here's what we found:

--Insert graph

## Meme stock forum correlation conclusion

There appears to be a strong correlation between the number of mentions to the performance of the meme stocks. The perception that the meme stocks are driven by the online forums seems to be true.

## Overall Conclusion

We come back to our original questions:

- Can Meme stocks stand up to a traditional financial analysis?
- Are Meme stock investors the same as crypto investors? Can this be proven by a negative correlation in their prices?
- Are Meme stock prices truly driven by forums such as wallstreetbets?
- Are Meme stocks a real money making opportunity?

Let's look at each one.

**_Can Meme stocks stand up to a traditional financial analysis?_**

Yes, they can. When checked for standard deviation, Sharpe Ratio and even by Monte Carlo simulations, the meme stocks performed very well. 

**_Are Meme stock investors the same as crypto investors?_**

Based on the analysis we performed, there appears to be no correlation between the performance of meme stocks and meme cryptos. It does not look like funds are flowing back and forth between these two. It seems, according to our data, that this idea is false. 

**_Are Meme stock prices truly driven by forums such as wallstreetbets?_**

Based on the data we scarped from the subreddits a correlation between mentions on the forums and meme stock performnce does exist. This may suggest a "chatter" strategy for meme stock investment. Rather than focus on the content in the online forums, perhaps assesing the amount of mentions, or "level of chatter" would be a good indicator of memestock direction. 

**_Are Meme stocks a real money making opportunity?_**

Based upon our analysis: yes, they can be. If the phenomena continues over the next tweleve months, it could be a very good opportunity. However, monitoring the volume of mentions or "chatter" in the online forums could be key. If the "chatter" starts to disappear, the opportunity gains may disappear as well. 












