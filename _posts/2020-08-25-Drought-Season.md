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
subject to long periods of no rain. The arrid, hot climate can contribute drastically to massive wildfires, as we have observed over the last year. 2019-2020
has been an unusually intense fire season, with locals dubbing it the "Black Summer" because of the volume of smoke filling the skies.

**How predictable is rain in Australia?**

Standard practice would dictate that I turn on the TV or favorite weather forecast site and wait to see if they were correct.
Short of installing a dopplar radar or high-tech satellite infrastructure, I decided to implement a few different Machine Learning models to see how well I can predict rain for the next day.

Using a history of weather readings from around Australia (*49 different locations, to be exact*) from 2007 through 2017, I determined there was a base rate of 70% for days with no rain, and about 30% of days with rain. Some rainy days had little to no rain (less than .2 mm) and others had quite a bit of rain ( more than 250 mm). With this baseline metric, I decided to answer the question: **Will it rain tomorrow?**

Because my question is a yes or no answer, my model would be a classification model rather than a regression model. The *target* I'm looking for the model to classify is whether its prediction is **Yes** it wil rain, or **No** it will not.



