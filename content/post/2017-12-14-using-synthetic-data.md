---
date: '2017-12-14'
title: Using Synthetic Data for Teaching Data Science
url: /2017/12/14/using-synthetic-data
tags: [synthetic-data data-science]
---


Hi Everyone, our paper called [*Teaching data science fundamentals through realistic synthetic clinical cardiovascular data*](https://www.biorxiv.org/content/early/2017/12/12/232611) is now available to read on Biorxiv.

In this paper, we talk about a dataset that we synthesized for teaching aspects of clinical data that may be tricky to understand in data science. This dataset is interesting because it's derived from a multivariate distribution based on real patient data, modeled as a Bayesian Network. Even when we knew true marginals for the real data, there was a lot of fine tuning to the Bayesian Network.

We've used this dataset for a couple of classes, and we've found that it helps highlight real issues in predictive modeling of clinical data. One of the largest is that most predictive models are based on a much older patient cohort (50+), which means that we don't know much about how to predict cardiovascular risk in younger patients. Part of the teaching exercise is having the students choose a cohort of interest and then attempt to predict on that patient cohort.

The data is currently available as an R package here, including vignettes about how the data was generated: https://github.com/laderast/cvdRiskData