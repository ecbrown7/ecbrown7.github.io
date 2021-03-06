Blog Post 4 - R Machine Learning Reflection
================

# **A Reflection on Machine Learning in R**

I found Random Forests most interesting. To explain why, I need to give
a little background. So there are currently &gt;10,000 chemicals in
production right now that humans may have exposure too (in drinking
water, skin products, plastic containers, etc). A majority of these
chemicals are actually untested and widely unregulated, and may present
a toxic hazard to humans. Part of the reason for that is that
traditional testing methods involving animal testing are slow and
expensive. There are several types of chemical toxins, but one of
particular increasing concern are endocrine disrupting chemicals (EDCs).
A common EDC that has been regulated is BPA, and you’ll notice that most
every plastic bottle you drink from will say ‘BPA Free’ on it. That is a
good start, but how many more are out there that we don’t know about
yet? There is good evidence to suggest an overall linear decline in male
testosterone rates since the 1970’s, and many point to the increasing
prevelance of EDCs as the root cause. Decreasing testosterone for men
can have significant health impacts, but EDCs really make their most
impact among the developing age population.

To combat these concerns, the US EPA formed the Endocrine Disrupter
Screening Program (EDSP) that aimed to shift the approach to chemical
regulatory assessment into a modern world. The result of the shift
relies on quantifying endocrine disruption using in-vitro
high-throughput screening (HTS) assays and integrating results across
wide-ranging chemical and biological endpoints using computational
models to develop a predictive approach. Ultimately, this approach is
designed to accomplish two goals, one short term and one long term. In
the short term, it aims to prioritize chemicals for further evaluation,
eliminating a large chunk that may waste decades with no effects in
animal testing and quickening our catch-up time to the mass of chemicals
currently untested. In the long term, it aims to use chemical predictive
features to model toxicity so as to make new chemical characterization
streamlined and effective.

I currently work on the assay development side, where we handle data
internally before collaborating with our modeling team. The modeling and
predictive toxicity side of things was never even remotely familiar to
me until taking this class and being exposed to Random Forests (ah,
lightbulb!). The modeler’s here at EPA use our data (and several other
data streams) along with 400+ chemical features (such as aromatic rings,
number of carbon-carbon double bonds, etc) from each chemical we test,
to train and test models for predictability. One of the most common
model types used is Random Forests. For example, a recent published
paper from a member of our lab on thyroid disruption used a Random
Forest model and the Gini index to rank COH\_alcohol\_aromatic\_phenol
as the most predictive chemotype, and the model predicted thyroid
toxicity with 76% accuracy.

Random forests are an extension of the bagging method as they utilize
bagging but also randomness to create an uncorrelated forest of decision
trees. The randomness comes in by generating a random subset of
features, which ensures low correlation among decision trees. In
comparison to a standard decision tree, random forests only select a
subset of those all features. We usually use something like CV to select
the number of predictors to use in the random forest model.Random
forests help to reduce the risk of overfitting, provide additional
flexibility and make it easier to determine feature importance (by say,
the Gini index, like in my example above).

Here, I’ll fit a random forest model on some simple car sample data to
give a quick demonstration of how it can work in R. We’ll try to predict
\# cylinders based on other automotive specs. Then, we’ll see which
predictors were most important to the prediction.

``` r
library(tidyverse)
library(caret)
library(randomForest)

data("mtcars")

mtcars$cyl <- as.factor(mtcars$cyl)

#Make things reproducible
set.seed(100)

#Split the data 70/30
split <- createDataPartition(y = mtcars$cyl, p = 0.7, list = FALSE)
training <- mtcars[split, ]
testing <- mtcars[-split, ]

#Fitting random forest model

rfFit <- randomForest(cyl ~ ., data = training, mtry = (ncol(training)/3), ntree = 200, importance = TRUE)

#Testing predictive accuracy
rfPred <- predict(rfFit, newdata = testing)
rfTest <- postResample(rfPred, testing$cyl)
rfTest
```

    ## Accuracy    Kappa 
    ##        1        1

``` r
#Plot the variable importance
varImpPlot(rfFit)
```

![](../images/unnamed-chunk-4-1.png)<!-- -->

Great, so we fit a random forest model and were actually able to get a
prediction accuracy of 1! This was a small data set with easy factor
predictions so that is not crazy. However, ranking the variable
importance was interesting. From the start, I thought that mpg would be
the best predictor of cyclinders (more cyclinders, lower mpg). But
actually, displacement was the best predictor. After a quick google
search, displacement is a direct measure of volume swept by all
cylinders in the car motor. Well if that’s not a direct predictor then I
don’t know what is.

Overall, nothing crazy here. But is was a neat check that the model told
us which variable was most predictive, similar to my real-world example
from earlier with the chemical feature.
