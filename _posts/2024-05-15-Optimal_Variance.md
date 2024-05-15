---
layout: post
title: Standard deviation in one pass and its impact on precision
subtitle: Optimization and its potential limitations study
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Stats, Python, R, Algorithms]
comments: true
---

{: .box-note}

## 1. Introduction
Lately during the interview I have reviewed an interesting problem about the optimization of the standard deviation calculation. Problem was well-known and was reviewed in an old Soviet book 
about [programmable calculators](https://www.xnumber.com/xnumber/russian_calcs.htm)[1].  In this post we will review the problem, its solution in Python and do a small study of the solution boundaries in terms of precision for different data. 

## 2. Problem description
Standard deviation of a probability distribution is defined as the square root of the variance σ². Where variance is the expected value of the squared deviation from the mean of a random variable.
Typical way to calculate it is to do two loops over the data:

```python
import math

def std_dev_two_loops(a):
    n = len(a)
    sum = 0
    sq_diff_sum = 0
	
    if n == 0:
        return 0
    
    for i in range(n):
        sum += a[i]		
    mean = sum / n
    
    for i in range(n):
        diff = a[i] - mean
        sq_diff_sum += diff * diff
    variance = sq_diff_sum / n
    
    return math.sqrt(variance)
```
But here we need to loop over the data twice and for the large data samples we might want to limit it to a single loop.

## 3. Solution
First lets rewrite the formula: 

![Formula for STD](https://github.com/vvzhukov/vvzhukov.github.io/blob/master/assets/img/Opt_STD_CodeCogsEqn.png?raw=true)   

And implement it in Python:  

```python
import math

def std_dev_one_loop(a):
    n = len(a)
    sum = 0
    sq_sum = 0
	
    if n == 0:
        return 0
    
    for i in range(n):
        sum += a[i]
        sq_sum += a[i] * a[i]
    mean = sum / n
    variance = sq_sum / n - mean * mean
    return math.sqrt(variance)
```
Now lets study and discuss potential limitations of such optimization.  

## 4. Studying precision for different data samples

Now lets check precision for different data sizes (thousand, million, and billion records), 
distributions (Normal, Poisson, Binomial, Chi-Square, Exponential,F) and outliers (Normal distribution, 5%, 10% outliers (±4SD)).  

We generated the random data, and reproduced the experiments 10 times to avoid potential random bias. You may find experiment results in the table below. Numbers dipict average absolute error between the *std_dev_one_loop()* and *std_dev_two_loops()* functions outputs.  

  
| Records | Normal | Poisson | Binomial | Chi-Squared | Exponential | F | Normal+Outliers 5% | Normal+Outliers 10% |
|---|---|---|---|---|---|---|---|---|
| Thousand 1E+03 | 0.0005 | 0.001084 | 0.000198 | 0.001524 | 0.0004965 | 0.000311 | 0.00064 | 0.00092 |
| Million 1E+06 | 1.00E-06 | 1.00E-06 | 2.00E-07 | 1.00E-06 | 5.00E-07 | 3.00E-07 | 1.00E-06 | 2.00E-07 |
| Billion 1E+09 | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* |  

*precision could be higher, was not able to capture (64 bit floating limitation). 

R code used to generate random records
```R
# control random for reproducabiliuty
set.seed(1001)

# 'n' Below is the sample size (10^3, 10^6, and 10^9)
# Normal
data_norm <- rnorm(n)

# Poisson
data_pois <- rpois(n,c(3,4,5))

# Binom
data_binom <- rbinom(n, size=1, prob=0.2)

# Chi-Square
data_chi_sq <- rchisq(n, df=5)

# Exponential
data_exp <- rexp(n)

# F
data_F <- rf(n, df1 = 10, df2 = 20)
```
All calculations were performed on the Linux VM with 20 logical processors @3.3Ghz and 32Gb of RAM.

## 5. Results

Based on the results we may conclude that optimized method *std_dev_one_loop()* have reasonable precision **±1E-3** on thousands of records,
high precision **±1E-06** on million records and extremely high precision **±1E-08** or higher on billion records. The worst preciesion was registered for the Poisson and Chi-Squared destribution.
Outliers did not impact the accuracy. Also in this post we have not studied the large numbers impact (our max outlier was 4SD from mean). That could be a major limitation for the described technique and we might come back to this problem to study it more.


## 6. References
1. Финк Л. Папа, мама, я и микрокалькулятор. — М.: Радио и связь, 1988)
2. https://www.strchr.com/standard_deviation_in_one_pass
3. https://www.xnumber.com/xnumber/russian_calcs.htm
4. https://www.johndcook.com/blog/2008/09/28/theoretical-explanation-for-numerical-results/
