Using APIs: Stocks vignette creation
================
Evan Brown

# **Project Links**

Link to regular repo: [Project 1:
Stocks_Vignette](https://github.com/ecbrown7/stocks_vignette)

Link to github pages repo:

# **Project 1 Wrap-up**

In this project, I created a vignette to show how to retrieve data from
an API. To demonstrate, I worked with the Polygon Financial API. Since
using a free Polygon account limits “from date” to 2 years, all of my
function calls and data were limited to 2 years from the completion date
of this project (2020-06-25 - 2022-06-25). To use as an example while
working with the API, I pulled data from a major constituent in the S&P
Oil & Gas Exploration & Production Industry, Valero Energy Corporation
(VLO). This industry reflects prices of major oil & gas companies and is
made up of 61 constituents, with Valero being one of the top 4
constituents, and a good indicator of the sector. Additionally, I pulled
data from 2 ETF’s, DRIP and GUSH, that reflect that industry. As a 2x
leveraged *inverse* ETF, DRIP price moves double the inverse of the
daily industry index, while GUSH is a standard 2x leveraged ETF and
moves with the index at double the daily rate. I used this data to
explore endpoints about market cap, price and volume for VLO, then
focused on price and volume relationship when comparing VLO to the
ETF’s. I grouped data by month, quarter and year at times, made some
plots, and drew some conclusions about what I found.

My first created function called ‘marketcap’ returns the marketcap for
the user input ticker and date. I used this function to pull data on VLO
marketcap from June 2020, 2021 and 2022 to explore trends over time. I
plotted that data as shown below. VLO has clearly has an impressive run
since 2020, increasing market cap year over year since then.

![](https://github.com/ecbrown7/stocks_vignette/raw/main/README_files/figure-gfmunnamed-chunk-6-1.png)

My second function called ‘dailyaggregate’ returns daily stock endpoints
for the user provided ticker across a user provided range of dates.
Several options exist in the function outside of ticker and date range
including a split adjustment option (true/false), a data sort option
(asc/desc), and a limit of returned results (default set to 5000). This
function also returns dates corresponding to the values alongside them,
and includes user friendly column names. The function must be used in
according to the users apikey access settings. With the free Polygon
account, the function will not work if the user passes a date more than
2 years prior to the active date.

I used the dailyaggregate function to return data from June 25, 2020 to
June 25, 2022 for VLO, DRIP and GUSH. To explore the data, I first took
an in depth dive at VLO and explored many aspects of the data. I created
an average price variable that reflects the average daily high and low
prices, then found the five number summary for that variable along with
all other endpoints of interest. While interesting, a single stock price
for 2 years of data needed to be broken down further.

As a result, I created new variables called month and quarter to group
the data in months and annual quarters. I then found summary statistics
for average price across both monthly and quarterly groups. I plotted
this data as box plots and found that quarter 2 has been the strongest
price quarter since 2020, with month 5 (May), being the single strongest
month.

![](https://github.com/ecbrown7/stocks_vignette/raw/main/README_files/figure-gfmunnamed-chunk-9-1.png)
![](https://github.com/ecbrown7/stocks_vignette/raw/main/README_files/figure-gfmunnamed-chunk-9-2.png)
Then, I created a histogram to look at which price ranges VLO spent the
most time in. The highest count was at 80 dollars, and counts above 100
were much lower than those less than 100 dollars.

![](https://github.com/ecbrown7/stocks_vignette/raw/main/README_files/figure-gfmunnamed-chunk-10-1.png)

I then created a variable called dailyperformance that categorized daily
stock movement as daily gain, daily loss, or no change. I created some
contingency tables based on this variable and broke it down by year and
month. VLO had more net losses in 2020, but more net gains in 2021 and
2022. However, the most interesting part was that total daily net gain
and losses were almost equivalent in the total date range evaluated (254
and 245 days, respectively). Pairing this with the increase in market
cap year over year suggests to me that the net gain days were large
gains, and the net loss days were small losses, a normal up and down
action for a bullish stock.

Finally, I compared price and volume in VLO, GUSH and DRIP. VLO price
showed that up and down bullish action, and the stock price in June 2022
is almost 50 dollars higher than in June 2020.

![](https://github.com/ecbrown7/stocks_vignette/raw/main/README_files/figure-gfmunnamed-chunk-14-1.png)
However, this was assumed based on the increasing market cap data. What
I was most interested in was the relationship between daily price and
daily volume. I calculated the correlation for VLO, GUSH and DRIP. The
correlations were as follows:  
- VLO: 0.10  
- GUSH: -0.59  
- DRIP: -0.45

That was very interesting to me. The industry common stock trading
volume has been relatively non-correlated with stock price. However, the
industry reflecting ETF trading volume has been strongly correlated with
ETF price. Just take a look at the plot for DRIP, the relationship is
hyperbolic.

![](https://github.com/ecbrown7/stocks_vignette/raw/main/README_files/figure-gfmunnamed-chunk-18-2.png)

That was a very cool find for me. In my view, it seems like we are at a
breaking point for the oil and gas industry stocks. They have been
propped up due to several national and international factors, but have
maintained a strong bullish run since recovering from the flash crash of
February 2020. DRIP is currently at it’s lowest price since that flash
crash, and volume is at an all time high. In addition, the most recent
scatter plot points for GUSH and VLO indicate a pullback in price. Could
we see a reversal from the bullish oil market to a bearish one? Only
time will tell for sure. But it seems like at least some people are
buying into DRIP reversing trend and going up in price.

# **Project 1 Reflection**

The most difficult part of the project in general for me was creating a
framework for what I was trying to accomplish. I wanted an outcome to
shoot for, not just blindly sifting through data. I had a long
brainstorming session to relate real world concepts to the data I was
going to be working with. It was rewarding in the long term doing it
this way, since the final project revealed meaningful data trends and
nice, share-able plots.

The most difficult part of the programming was adding dates to my
aggregate function. Pulling data from the API didn’t include a dates
column, but I wanted to look at the data based on months, quarters and
years to get distinct breakdowns. Since the market isn’t open 24/7, 365,
I obviously made this tougher on myself than I needed to. I had to
create a string a dates, then find a way to remove weekends and holiday
closures. Removing weekend was fairly efficient, but removing holidays
was hard coded in. I could have typed a string of all holidays for the
next 10 years to increase the function lifetime, but I’m sure we’ll have
new holidays by then and I’d need to fix them anyways. Nevertheless, the
function works for any date range (within 2 years) in 2020 - 2022. In
the end, it does it’s job for querying the API, returning the data
you’re looking for, and allowing you to do data analysis. I’ll just have
to update the holiday exceptions as years go on to ensure dates are
matching and vector lengths of retrieved data and dates are of equal
length.

I felt my approach was good overall for this project. However, I
probably would have spent more time writing things out on paper before
trying to code in ideas, only to have them not work and realize I wasted
an hour or two. But, that’s the nature of coding. Sometimes banging my
head against the wall leads me to an understanding of why something
doesn’t work, which points me to why something else does work - and in
the end, I gain a much better understanding of the material.

In conclusion, I thought the project was alot fo work, but rewarding for
me. I was able to touch on almost every single aspect of coding we’ve
covered thus far in ST558. I am happy with the resulting project and am
excited to continue learning more about R and data science. Also, I am
not a financial advisor, so it is not recommended to take my advice on
whether or not to buy DRIP right now but - “buy low, sell high” sure
does fit the market right now.
