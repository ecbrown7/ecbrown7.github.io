Project 2: Automated-modeling
================

# **Project Links**

Link to Project: [Project](https://ecbrown7.github.io/ST558_project2/)

Link to Repository: [Repo](https://github.com/ecbrown7/ST558_project2)

Links to specific news channel reports:  
[Business](https://github.com/ecbrown7/ST558_project2/blob/main/bus.md)  
[Entertainment](https://github.com/ecbrown7/ST558_project2/blob/main/entertainment.md)  
[Lifestyle](https://github.com/ecbrown7/ST558_project2/blob/main/lifestyle.md)  
[SocMed](https://github.com/ecbrown7/ST558_project2/blob/main/socmed.md)  
[Technology](https://github.com/ecbrown7/ST558_project2/blob/main/tech.md)  
[World](https://github.com/ecbrown7/ST558_project2/blob/main/world.md)

# **Project Wrap-up**

The basis for Project 2 involved us reading in data on news article
shares with several corresponding predictors. We then explored the data
by creating several summary statistics and plots. Then, we fit 3 linear
regression models, 1 random forest model, and 2 boosting trees models.
We made comparison for these models and selected a winning model on the
criteria of RMSE. Then finally, we wrapped it up by automating the
report for each news channel in the main data set, creating 6 reports,
one for each channel.

*What would I do differently?*

It was certainly challenging dealing with such a large amount of
predictors and sifting through to find ways to model the data. There
would really be endless models you could fit, we decided on 6 total
models but even these 6 results in a some different “winning models” for
each channel (Three channels were best fit by linear model 2, two
channels best fit by linear model 3, and one channel was best fit by our
first boosted tree model). Looking back, trying 30 models would have
been just as easy once we automated the comparison portion.

*What was the most difficult part for me?*

As always, the most difficult part for me is getting a game plan in my
head before starting off. In some ways, I wanted to just fit the models
first to decide which one was going to be the best so I could tailor our
plots around that. However, needing to automate took that option away.
It was obviously important that we made plots and models that could
withstand different inputs and not be tied down to the data of a
specific channel. For example, as I worked through the box plots for the
daily news shares…
![](https://github.com/ecbrown7/ST558_project2/blob/main/README_files/figure-gfmunnamed-chunk-8-1.png)

I started to realize there were some outliers that made the boxplots
unreadable. Easy fix, I thought. Just set the y axis limit to 10,000 and
move on. However, we worked through the first plots in the ‘bus’
channel. When we got to the lifestyle channel, the y axis needed to be
over 20,000 to capture most of the data. In turn, we had to create a way
to capture “most of the data” in our plots in an automated fashion. We
decided to take the 98th quantile and make it the y axis for each plot.
In doing so, we automated each news channel to have a plot that showed
98% of the data but resisted the outliers from making our plots
unreadable. I think that really changed the way the visual part of the
project turned out.

*Big take-aways*

Couple things. Number one was mentioned above but to keep it brief - it
was learning to navigate automation for multiple plots. This is the
first time we’ve really been challenged to make a plot that mendable to
multiple inputs and not on fixed scaled. Secondly, learning to work with
a partner on a coding project through GitHub was different. I think it
went fairly smoothly for both of us (at least it did for me), but it was
definately different having to use the pull functionality and not just
the push. Third, I got to play around with some plots in here and I was
really happy with how my sentiment polarity plot turned out.
![](https://github.com/ecbrown7/ST558_project2/blob/main/README_files/figure-gfmunnamed-chunk-9-1.png).

I knew I wanted to make this more than just a black dotted scatter plot
because the x axis was a scale, and I felt it needed color coding. It
was challenging getting this set up, especially learning how to fix the
axis as the color scale and not just the points. But once we got it up
and going, it was easily applied to the rest of our plots. I think this
is something I will use in the future for scaled predictors like this. I
was hoping to have a political channel in here where the plot could
really make use of the far positive and far negative sides of sentiment
polarity but most things seemed to be fairly neutral for these news
channels.

Overall, I thought Daniel and myself worked well together and both
contributed to a quality, informative automated-modeling project. I am
happy with the results and all that I learned in the process.
