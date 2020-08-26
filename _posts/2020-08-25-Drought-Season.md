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

Using a history of weather readings from around Australia (*49 different locations, to be exact*) from 2007 through 2017, I determined there was a base rate of 70% for days with no rain, and about 30% of days with rain. Some rainy days had little to no rain (less than .2 mm) and others had quite a bit of rain ( more than 250 mm). With this baseline metric, I decided to answer the question: **Will it rain tomorrow?**

Because my question is a yes or no answer, my model would be a classification model rather than a regression model. The *target* I'm looking for the model to classify is whether its prediction is **Yes** it will rain, or **No** it will not.

<h4>Cleaning and Wrangling</h4>
Although this dataset was relatively clean, there were certain features which needed to be dealt with in order to feed it into a machine learning model. Many features had missing data, but there was quite a few that actually had about *half* of their data missing. I ended up dropping those features altogether, because trying to impute those missing values would prove to be too cumbersome. Other features, which weren't so void of true data were imputed using a "most frequent" strategy. 

Because most of the data was time-series sequential, and my target was only a days difference away, I could shift the data one day and create a classification target that was capable of being predicted by my models. 

<h2>Target</h2>
Each day's observation as a "Rainfall" amount in millimeters. By setting my threshold to .3 mm, I found I could balance my classes 

<h2>Time-Series Challenges</h2>
Normally, time-series data requires extra care to account for what they call "lagging variables". The variables (cloud cover, dropping barometric pressure, etc) are all indicators of rain, but sometimes rain is not immediate. Because of the nature of time-series data, it is important to check for cyclic trends or seasonality when figuring how to forecast. 

Fortunately for me, the problem I set out to solve was not one of long term forecasting. My question was simple: Given the variables of any given day, will it rain the following day?
This can

