Blog Post 5: ST558 Course Reflection
================

# **Final Blog Post**

### Thoughts on R and plans to use in the future?

I really like using R. For one, it’s great for me that it’s free to use.
For two, collaboration has been easy for me and I love the flexibility
in the language. And for three, it’s really limitless and it has been
neat to look at all the different things R can be used for. I will
definitely continue to use R going forward. I use it at work frequently
already and certainly plan to keep going in that direction. Since I’m
always on the front end planning and running experiments at work,
learning R has allowed me to take over internal data analysis and has
really streamlined our work by giving me the reigns on experiments from
end to end.

### Things to do differently now that I know R

As I’ve mentioned before, I was very excited to start this class to
really gain the skills necessary to run experiments end to end in our
lab. Since about the midterm in this class, I’ve been able to get going
with R at work and have analyzed data of two chemical screens, one using
some EPA packages (tcpl) for fitting hill curves and the other using
ggplot to create boxplots looking for shifts in chemicals. The boxplot
screen in particular was neat for me. We started this screen the week
this class started, which unfortunately coincided with my visit to the
emergency room (thanks again for the leniency on HW2). Throughout that
recovery process was a constant struggle to get the data collected for
this screen while maintaining my effort in this class. To wrap it all up
by actually using what I had learned in this class to analyze the data
was really rewarding and something we plan to continue going forward.
And hopefully without any more ER visits!

### Areas of statistics/data science to explore further

A couple things are on the back burner right now. First, at work we have
some R code that will output log spaced dose concentrations and
something called alt-log spaced doses that is useful for screening
chemicals when we evaluate cyps. Alt-log shifts the doses closer
together towards the top end of the dose range where most cyp activity
occurs, that way we can get a better feel for exactly where the activity
is taking place. This isn’t straightforward, and for some people
designing experiments who aren’t familiar, it can be confusing. Now that
I know shiny, people just want to use me!! - but I’ve been asked to
create a shiny app that people can use where experiment designers can
just input their top and bottom concentrations, number of
concentrations, and select log or alt-log spacing, and then get returned
a table of the concentrations they should use. Prety simple and
straightforward.

For statistics, I’m obviously interested in learning more in general as
I begin the masters program next semester. In particular, I have enjoyed
learning certain tests and statistical values that are industry
specific. For example, we use a Z prime (Z’) metric for evaluating an
assay’s effectiveness. This metric is 1 - (3 x standard deviation from
the top concentration + 3 x std dev vehicle control)/(signal from top -
control). This gives a value of 1 at the top end and values \>0.5 are considered
a good working assay, while an assay \<0 is a bad, non functional assay.
Areas in the middle are typically a grey area where the assay may be
able to be improved in some ways to make a working one. As I learning
new things from this statistics program, it is ever more interesting to
find ways to apply them to research at work and get practical use in
applying them.

Finally, for myself - I’m big into the outdoors, hunting, fishing, etc.
Growing up around it, you learn that animals change their behavior a lot
depending on the weather. However, there are some stronger indicators
than other. For example, deer in the fall tend to be much more active
overall when the temperature is colder. This is well agreed upon.
However, some people will also say they’re more active in the daytime
when the moon is closer to full, more active in evenings when pressure
is high, etc. I’ve had an idea to capture deer activity metrics and
model that to all the different weather predictors. I know of one app
out there that tries to do something like this, but obviously their
formulas are “top secret”. They’ll basically just give you a prediction
of deer activity (high, medium, low) based on weather in your region of
the country. Then as a user, you can choose the high days to go sit and
the low days you can sit at home, etc. Great idea to take peoples money
but I don’t necessarily trust it for two reasons: for one, the app was
developed in the Midwest, so I’m unsure of how much research was done
here in the east, and for two, animal activity can differ from farm to
farm, so regional classification that includes both the Carolina,
Virginia, Tennessee, and Georgia doesn’t sound very specific or
necessarily effective. I’ve thought about doing something small scale on
our own farms to develop a predictive model for personal use - hopefully
increasing chances of seeing stuff when in the woods. Obviously the most
challenging part of this is going to be capturing activity through the
use of visuals, trail cameras, etc when I don’t have the budget to
tranquilize and collar track deer. But, we’ll see how it goes on my
“extra spending money” budget and hopefully it turns up something
useful - I’m sure I will at least like going through the process of
attempting this and then maybe flesh out some further ideas for when I
no longer have to pay for grad school and can roll some more funds this
way!

I have really enjoyed this course, thank you for all the support!
