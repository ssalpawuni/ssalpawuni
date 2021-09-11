---
title: 'Tutorial 2: Worked Examples'
author: Abubakari Sumaila Salpawuni
date: '2021-09-11'
slug: tutorial-2-worked-examples
categories: [Question and Answers]
tags: [maximum likelihood, methods of moments, skewness]
subtitle: ''
summary: 'Solving selected problems around methods of moments, maximum likelihood, statistical independence etc.'
authors: []
lastmod: '2021-09-11T22:39:53+03:00'
featured: no
image:
  caption: 'Image credit: [**Leon Wu**](https://unsplash.com/photos/LLfRMRT-9AY)'
  focal_point: ''
  preview_only: no
projects: []
url_code: "uploads/tutorial_2_salpawuni.tex"
url_dataset: ""
url_pdf: "uploads/tutorial_2_salpawuni.pdf"
---



## Introduction

This is the second tutorial of common problems in Statistics alongside their suggested solutions. No particular level is the target. Thus, you may find any of the problems to be at any of the levels (undergrad, master's, or doctoral level). For example, the first question comes from the [University of South Carolina](https://sc.edu/study/colleges_schools/artsandsciences/statistics/index.php), Department of Statistics (PhD level). In some cases, it may be difficult to cite the exact source of the question. So in cases where I am certain of the original source of the question, I would do my best to cite the source of it. If you feel any of the sources is not properly cited, please draw my attention to it.

## Problem 1

Suppose $X_1, X_2, X_3, \ldots, X_n$ is an *iid* sample from uniform distribution over $(\theta, \theta + \vert \theta \vert)$, where $\theta \neq 0$.

a). Find the method of moments estimator of $\theta$,

b).  Find the maximum likelihood estimator (MLE) of $\theta$.

{{< spoiler text="Source" >}} [University of South Carolina, PhD Qualifying Exams](https://sc.edu/study/colleges_schools/artsandsciences/statistics/index.php) {{< /spoiler >}}

## Solution 
a).

Given that $X_i \overset{iid}{\sim} Unif(\theta, \theta + \vert \theta \vert), \quad \theta \neq 0$. For moments, generally, $M_k^* = \frac1n \sum_{i=1}^n X_i^k$  is the $k^{th}$ sample moment, for $k= 1, 2, \ldots$. This implies $M_1^* = \frac1n\sum_{i=1}^n X_i = \bar{X}$

\begin{equation*}
\begin{split}
E(X) &= M_1^*\\\\
&= \frac{\theta + \theta + \vert \theta \vert}{2} = M_1^*\\\\
&= \theta + \frac{\vert \theta \vert}{2} = M_1^*\\\\
&= \frac32\theta I_{(\theta > 0)} + \frac\theta2 I_{(\theta < 0)}
\end{split}
\end{equation*}
Note that $M_1^* = \bar{X},\quad \mbox{and}\quad  P(\bar{X} >0 \vert \theta > 0) =P(\bar{X} < 0 \vert \theta < 0) = 1$. Solving for each condition (on $\theta \neq 0$), we have;
\begin{equation*}
\therefore \hat{\theta} = \frac23\bar{X} I_{(\bar{X}>0)} + 2\bar{X} I_{(\bar{X} < 0)}
\end{equation*} 

b).

The distribution of $X_i$ can be considered for both sides (i.e, $\theta >0$ and $\theta <0$ such that;
\begin{equation*}
X_i \sim 
\begin{cases}
Uniform(\theta, 2\theta) & \mbox{if}\quad \theta > 0\\\\
\\\\
Uniform(\theta, 0) & \mbox{if}\quad \theta  < 0
\end{cases}
\end{equation*}
Their likelihood functions are thus,
\begin{equation*}
f_X(x;\theta) = 
\begin{cases}
\frac{1}{\theta^n} I\left(\frac{X_{(n)}}{2} \le \theta \le X_{(1)}\right) & \mbox{if}\quad \theta  > 0\\\\
\\\\
\frac{1}{\vert\theta^n\vert} I\left(\theta \le X_{(1)}\right) & \mbox{if}\quad \theta  < 0\\\\
\end{cases}
\end{equation*}
The maximum likelihood estimator, $\theta$,  is therefore the *order statistic*;
\begin{equation*}
\begin{cases}
\underset{\theta > 0}{argmax} \quad f_X(x;\theta) = \frac{X_{(n)}}{2}\\\\
\\\\
\underset{\theta > 0}{argmax} \quad f_X(x;\theta) = X_{(1)}\\\\
\end{cases}
\end{equation*}

\begin{equation*}
\therefore \hat{\theta}_{\mbox{MLE}} = \frac{X_{(n)}}{2} I_{(X_1 > 0)} + X_{(n)} I_{(X_1 < 0)}  
\end{equation*}

## Problem 2

The density function of a random variable is 
\begin{equation*}
f(x) =
\begin{cases}
\frac{4}{81}x(9-x^2), & 0 \le x \le 3\\
\\\\
0, & \mbox{elsewhere}
\end{cases}
\end{equation*}

a) Find the mode, b) the median, c) compare the mode, median, and median

{{< spoiler text="Source" >}}  Dokuz Eylul University, Assignment{{< /spoiler >}}


## Solution

Check to see if there exists a mode, equate $f^\prime(x)$ to zero (maximum value), checking that $f^{\prime\prime}(x) < 0$
\begin{equation*}
\begin{split}
f(x) = \frac{4}{81}x(9-x^2) & \implies f^\prime(x) =  \frac{\partial f(x)}{\partial x} = \frac{1}{81}(36 - 12x^2)\\\\
&\implies  f^{\prime\prime}(x) = -\frac{ 24x}{81} < 0\quad \mbox{(mode extists)}\\\\
\end{split}
\end{equation*}

a). mode

\begin{equation*}
\begin{split}
&f(x) = 0\\\\
&\frac{4}{81}(9 - 3x^2) = 0\\\\
&\therefore x = \sqrt 3
\end{split}
\end{equation*}

b). median

\begin{equation*}
\begin{split}
F(m) &= 0.5\\\\
P(x \le m) &= 0.5\\\\
& = \frac{4}{81} \int_0^m (9x-x^3) =  0.5 \\\\
& = \frac{4}{81}\left(\frac92x^2-\frac14x^4\right)\bigg\lvert_0^m =  0.5\\\\
& = 72m^2 - 4m^4 =  162\\\\
& = 2m^4 - 36m^2 + 81 = 0
\end{split}
\end{equation*}
Solving the quadratic equation in $m^2$, i.e., ($ax^2 + bx + c = 0$);

\begin{equation*}
\begin{split}
m^2 &= \frac{-b \pm \sqrt{b^2-4ac}}{2a}\\\\
&= \frac{36 \pm \sqrt{36^2-4\cdot 2\cdot 81}}{2\cdot 81}\\\\
&= 9 - \frac92\sqrt{2}\quad \mbox{or}\quad 9 + \frac92\sqrt{2}\\\\
m^2 & = 9 - \frac92\sqrt{2}\\\\
m &= \sqrt{9 - 9/2\sqrt{2}} = 1.6236\\\\
\therefore\quad &\mbox{the median is}\quad \mathbf{1.6236}
\end{split}
\end{equation*}

c). comparison

\begin{equation*}
\begin{split}
E(X) & = \int f(x)dx = \int_0^3 x\cdot\frac{4}{81}x(9-x^2)dx\\\\
&=  \frac{4}{81}\left(3x^3 + \frac15x^5\right)\bigg\lvert_0^3\\\\
&= \mathbf{1.60}
\end{split}
\end{equation*}

Since $\mbox{mean} <\mbox{median} <\mbox{mode}$, the distribution of $X$ is said to be *skewed* to the left.

## Problem 3

Let $\bar{X}$ and $S^2$ be the mean and variance of a random sample of size $25$ and $X\sim N(3, 100)$. Find $P(0 < \bar{X} < 6, 55.22 < S^2 < 145.6)$

{{< spoiler text="Source" >}} Exact source not clear {{< /spoiler >}}

## Solution

$\mu = 3, \sigma^2 = 100$. Since $\bar{X}$ and $S^2$ are independent, we have;
\begin{equation*}
P(0 < \bar{X} < 6, 55.22 < S^2 < 145.6) = P(0 < \bar{X} < 6) \times P(55.22 < S^2 < 145.6)
\end{equation*}
\begin{equation*}
\begin{split}
P(0 < \bar{X} < 6) & = P\left(\frac{0 - 3}{\sqrt{\frac{100}{25}}} < z < \frac{6 - 3}{\sqrt{\frac{100}{25}}}\right)\\\\
&= P(-1.5 < z < 1.5) \\\\
&= 0.8664\\
\end{split}
\end{equation*}

\begin{equation*}
\begin{split}
P(55.22 < S^2 < 145.6) & = P\left( \frac{155.2\times 25}{100} <\frac{nS^2}{\sigma^2} < \frac{145.6\times 25}{100}\right)\\\\
& = P(13.8 < \chi_{24}^2 < 36.8)\\\\
& = 0.95 - 0.05\\\\
& = 0.90
\end{split}
\end{equation*}

\begin{equation*}
\therefore P(0 < \bar{X} < 6, 55.22 < S^2 < 145.6) = 0.8664 * 0.90 = \mathbf{0.8231}
\end{equation*}

#### Did you find this post helpful? Consider sharing it😊😊😊
