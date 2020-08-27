---
layout: post
title: Drought Season
subtitle: Predicting Rain in the land Down Under
gh-repo: paulteeter/
gh-badge: [star, fork, follow]
tags: [Data Science, Lambda, Data, Mildly Interesting]
comments: true
---

"Rain Rain, Go away..."

It's an innocuous childhood favorite for many, but the reality in Australia proves how dangerous and deadly a drought can be. Large parts of Australia are often
subject to long periods of no rain. The arid, hot climate can contribute drastically to massive wildfires, as we have observed over the last year. 2019-2020
has been an unusually intense fire season, with locals dubbing it the "Black Summer" because of the volume of smoke filling the skies.

**How predictable is rain in Australia?**

Standard practice would dictate that I turn on the TV or favorite weather forecast site and wait to see if they were correct.
Short of installing a dopplar radar or high-tech satellite infrastructure, I decided to implement a few different Machine Learning models to see how well I can predict rain for the next day.

Using a history of weather readings from around Australia (*49 different locations, to be exact*) from 2007 through 2017, I determined there was a base rate of 77.5% for days with no rain, and about 22.5% of days with rain. Some rainy days had little to no rain (less than .2 mm) and others had quite a bit of rain ( more than 250 mm). With this baseline metric, I decided to answer the question: **Will it rain tomorrow?**

Because my question is a yes or no answer, my model would be a classification model rather than a regression model. The *target* I'm looking for the model to classify is whether its prediction is **Yes** it will rain, or **No** it will not.

<h2>Cleaning and Wrangling</h2>
Although this dataset was relatively clean, there were certain features which needed to be dealt with in order to feed it into a machine learning model. Many features had missing data, but there was quite a few that actually had about *half* of their data missing. I ended up dropping those features altogether, because trying to impute those missing values would prove to be too cumbersome. Other features, which weren't so void of true data were imputed using a "most frequent" strategy. 

Because most of the data was time-series sequential, and my target was only a days difference away, I could shift the data one day and create a classification target that was capable of being predicted by my models. 

The original dataset already had a target created, called *RainTomorrow*, which was based on the feature *RISK_MM*. The original dataset had a threshold of 1.0mm of rain determing whether it was classified as rain or not. But this created imbalanced classes (77/23%). 

<h4>Target</h4>
Each day's observation has a "Rainfall" amount in millimeters. By setting my threshold to .2 mm, I found I could balance my classes a little more evenly, while still accounting for days when it was misty or drizzled a tiny amount to not be classified as "rain". This new feature target '*ExpectRain*' had a baseline classification score of **64.1% No**,  **35.9% Yes**. 


<h4>Time-Series Challenges</h4>
Normally, time-series data requires extra care to account for what they call "lagging variables". The variables (cloud cover, dropping barometric pressure, etc) are all indicators of rain, but sometimes rain is not immediate. Because of the nature of time-series data, it is important to check for cyclic trends or seasonality when figuring how to forecast. 

Fortunately for me, the problem I set out to solve was not one of long term forecasting. My question was simple: Given the variables of any given day, will it rain the following day?

This problem is easily solved through shifting the data 1 day to adjust for the lagged variable. The new target was based on the following day's "Rainfall" amount.

<h4>Data Leakage</h4>
There were a few features that had potential to create leakage into the model. Obviously my target feature was removed from the training data, but the shifted variable *'RISK_MM'* and the *'Rainfall'* amount had opportunity to leak into the model and skew the outcome and were removed from the training data as well.

<h2>Modeling</h2>

For a binary classification problem, I chose to fit three different models to see how each performed. My first model was a Decision Tree Classifier. While it made an improvement over the baseline classification, it was not the best performing model. With a validation accuracy of **74.87%**, the model is useful but not great.

For my second model, I chose a Random Forest Classifier. This model had a slight improvement over the standard Decision Tree, with a validation accuracy of **75.93%**. This was the best performing model, which I used later to predict on my test data.

I also chose to fit a Logistic Regression model, so I could see how a linear model would perform in this task. This was the worst performing model, with a validation accuracy of only **72.91%**. 

Due to overfitting concerns, I refrained from too much hyperparameter tuning to keep my models as generalized as possible. Mostly the tuning was changing the number of iterations, the maximum depth of the model (from root to leaf), and the minimum samples per leaf. Depsite each model only having marginal improvements over the baseline score, I decided not to push too hard in fear that I would overfit on my training data and have a worse accuracy for my testing data.


<h2>Final Test Scores</h2>

After determining that the RandomForest model performed the best, I predicted the outcomes on the training data and checked its accuracy. The final test data accuracy was **74.35%**, which is quite a surprise. I figured my model would be a little better at predicting, but that it was relatively low is indicitive of how difficult it is to predict rain and that the training data was overfit.


<h4>Explaining Model Performance</h4>

As seen below in the Partial Dependence Plot with an isolated feature, the variation amongst the single feature is so great, its not hard to imagine why the model has a hard time predicting with great accuracy. This feature (Temperature at 3PM) has the most positive impact on the models ability to classify properly, but even with its positive trend, the variation is so great, its quite apparent the model would have a difficult time accurately predicting whether it would rain tomorrow or not. In this PDP isolate, at each value on the X Axis, all of the observations for the other inputs are evaluated for the model and the output is averaged, giving us the highlighted line.
Take note that this is not a direct coefficient on the feature at a given value, but rather a representation of how all of the other inputs affect the target variable in the model.
<br /><br />
<div id="wrapper">
  <div class="container">
    <img class="image" src="/assets/img/PDP_Isolate.png" alt="PDP Isolate" />
  </div>
</div>
  
Another way to see how each feature had impact on the models output is with this handy Shapley Value Summary Plot: <br />
<div id="wrapper">
  <div class="container">
      <img class="image" src="/assets/img/shap_summary.png" alt="Shapley Value Summary Plot" />
  </div>
</div>
Its quite apparent that most of the features have a relatively minor impact on the model's decision from the baseline guess, but a few features have a little bit more impact, both positive and negative, depending on how the models decisions are being structured.


Here is the same shapley plot for an individual observation, to see how each feature affected the model's probability.
<div id="wrapper">
  <div class="container">
      <img class="image" src="/assets/img/ind_shap_plot.png" alt="Shapley Forceplot for Individual Observation" />
  </div>
</div>
In this single obervation, the model had a 90% probability of classifying this properly, because of the features in **RED** that increased the models output probability from the baseline of 64% to 90%.
