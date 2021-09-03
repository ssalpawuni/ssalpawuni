---
title: Let's talk briefly about Bayesian Statistics
author: Abubakari Sumaila Salpawuni
date: '2021-08-31'
draft: true # added by me!
slug: let-s-talk-briefly-about-bayesian-statistics
categories: ["R"]
tags: ["R", "Bayesian Statistics", "conjugate priors"]
subtitle: ''
summary: ''
authors: []
lastmod: '2021-08-31T20:36:33+03:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

In Statistics, estimating the uncertainty of an unknown quantity is a core
problem. Broadly speaking, dealing with this can take one of two paths, or even
both -- Frequentist estimation or Bayesian estimation. It is worth noting, however,
that these two approaches fundamentally have different inference schemes about
how they express `degree of belief`, and needless to say, there is a
raging 2-century-old debate over what probability means. In this post, I
will be briefly focusing on Bayesian statistics, with demonstration in `R`. Basic
knowledge of Statistics is assumed. Further to that, I assume you have, at least,
a basic working familiarity with analysis in `R`.

Let's assume I show you a flip coin and exclaimed; 'Look! This coin in my hand
is unbias'. But you are not the type of people accepting mere assertions
without overwhelming evidence. So to accept my claim, you demand that we toss
the coin, say, 1000 times, and count the number of times 'heads' showed up
relative the number of 'tails' produced. Now, if my claim were right, we expect a
close proportions of heads and tails, say for example, 510-heads to 490-tails. However,
if in a 1000-toss, it turned out that, 999 cases landed on a 'head', and only one
landed on a 'tail', then you would have had an overwhelming evidence against my claim,
and outright rejecting the claim of 'unbiasedness'. Even if the probability of
head were 0.75 or 0.15 or some value other than 0.50, that would still be a
piece of evidence against my claim. To express this statistically, we may
represent this experiment as one that follows a binomial distribution as;


$$X_n \sim \mbox{Binom}(\theta, n)$$;
where $\theta$ is the probability of landing a head (parameter), and $n$ is the
number of flips.

Referring to the representation above, if we consider $\theta$ in the classical
setting, then it absolutely makes no sense to ask a question like
$P(\theta_1 < \theta < \theta_2|X_n, n) = ?$. This is because, the frequentist
approach treats the parameter as fixed quantity with no room for variation, and
can only be estimated through repeated sampling, under identical conditions. Thus,
the frequentist method depends on the long-run frequency of the trials. In contrast,
for Bayesian setting, the fact that a parameter is fixed is completely rejected
in that, it is treated as a random variable having some probability distribution.
In fact, we start estimation with an initial belief (called the `prior`) before we
even observe the data. After looking at the data, our belief of the parameter (estimation)
is *updated* (posterior). It is because of the subjective nature of the 'initial belief' that
makes many frequentist enthusiasts criticize the Bayesian method. However, Bayesian
 statisticians have refuted this criticism to positing that, in a decision making
 where uncertainty present, it's better to explore all scenarios in a rigorous and
 coherent manner. I should point out immediately that, these two approaches are not in
 reality contradictory, but only presents two different angles of addressing the
 problem.

# Template for Bayesian inference
In this section, I will briefly illustrate the 'prototype' of a Bayesian statistical
inference. Let $\theta$ represent a parameter of interest which is considered unknown.
Furthermore, let $y$ be the observed data. Therefore, a Bayesian inference can be
formulated as;

$$p(\theta\vert y) = \frac{p(\theta) p(y\vert \theta)}{p(y)}$$, where;


- $p(\theta)$ is the `prior`. The plausible values of $\theta$ before we see the data
- $p(y\vert \theta) = L(\theta; y)$ is the likelihood. The sampling distribution relative
to the unknown parameters.
- $p(\theta\vert y)$ is the `posterior`. After seeing the data, what is our updated belief.
- $p(y)$ is the `normalizer`. A constant that is of less importance to the modeling process

## example
In a certain population, it is believed that $1.5\%$ of the population has
disease X. Assuming health providers in that community decide to embark on a
free-screening exercise for the said disease. And it is known that, for a person who
has the disease, the test has accuracy of $97\%$ for a positive test result. Also, for
a person who does not have the disease, the test has accuracy of $95\%$ for a
negative test result. Assuming you presented yourself for testing and your test result
came positive for the disease. what is the  probability that you actually have the disease?

This is clearly a Bayesian problem with the following pieces of information;

$P(D) = 0.015$; $P(T^+\vert D) = 0.97$; $P(T^-\vert D^\prime) = 0.95$
We're interested in $P(D\vert T^+)$. Using the Bayesian formulation, we have;

$$P(D\vert T^+) = \frac{P(D)P(T^+\vert D)}{P(D)P(T^+\vert D) + P(D^\prime)P(T^+\vert D^\prime)}$$
