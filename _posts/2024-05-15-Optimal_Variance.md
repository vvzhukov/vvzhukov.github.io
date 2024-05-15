---
layout: post
title: Standard deviation in one pass and its impact on precision
subtitle: Optimization and its potential weaknesses study
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Stats, Python, R, Algorithms]
comments: true
---

{: .box-note}

## 1. Introduction
Lately during the interview I have reviewed an interesting problem about the optimization of the standard deviation calculation. Problem was well-known and was reviewed in an old Soviet book 
about [programmable calculators](https://www.xnumber.com/xnumber/russian_calcs.htm).  In this post we will review the problem, its solution in Python and do a small study of the solution boundaries in terms of precision for different data. 

### 2. Problem description
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

  
| | Normal | Poisson | Binomial | Chi-Squared | Exponential | F | Normal+Outliers 5% | Normal+Outliers 10% |
|---|---|---|---|---|---|---|---|---|
| thousand records | 0.0005 | 0.001084 | 0.000198 | 0.001524 | 0.0004965 | 0.000311 | 0.00064 | 0.00092 |
| million records | 1.00E-06 | 1.00E-06 | 2.00E-07 | 1.00E-06 | 5.00E-07 | 3.00E-07 | 1.00E-06 | 2.00E-07 |
| billion records | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* | 1.00E-8* |  

*precision could be higher, was not able to capture (64 bit floating limitation). 

R code used to generate random records
```R
# control random for reproducabiliuty
set.seed(1001)

# Normal
data_norm_1k <- rnorm(10^3)
data_norm_1m <- rnorm(10^6)
data_norm_1b <- rnorm(10^9)
# Poisson
data_pois_1k <- rpois(10^3,c(3,4,5))
data_pois_1m <- rpois(10^6,c(3,4,5))
data_pois_1b <- rpois(10^9,c(3,4,5))
# Binom
data_binom_1k <- rbinom(10^3, size=1, prob=0.2)
data_binom_1m <- rbinom(10^6, size=1, prob=0.2)
data_binom_1b <- rbinom(10^9, size=1, prob=0.2)
# Chi-Square
data_chi_sq_1k <- rchisq(n=10^3, df=5)
data_chi_sq_1m <- rchisq(n=10^6, df=5)
data_chi_sq_1b <- rchisq(n=10^9, df=5)
# Exponential
data_exp_1k <- rexp(n=10^3)
data_exp_1m <- rexp(n=10^6)
data_exp_1b <- rexp(n=10^9)
# F
data_F_1k <- rf(10^3, df1 = 10, df2 = 20)
data_F_1m <- rf(10^6, df1 = 10, df2 = 20)
data_F_1b <- rf(10^9, df1 = 10, df2 = 20)
```
All calculations were performed on the Linux VM with 20 logical processors @3.3Ghz and 32Gb of RAM.

## 5. Results

Based on the results we may conclude that optimized method std_dev_one_loop() have reasonable precision ±10^3 on thousands of records,
high precision ±10^6 on million records and extremely high precision on billion records. The worst preciesion was registered for the Poisson and Chi-Squared destribution.
Outliers did not impact the accuracy. Also in this post we have not studied the large numbers impact (our max outlier was 4SD from mean). That could be a major limitation for the described technique and we might come back to this problem to study it more.


# 6. References

 https://www.strchr.com/standard_deviation_in_one_pass
 https://www.xnumber.com/xnumber/russian_calcs.htm
 https://mathworld.wolfram.com/StandardDeviation.html
 https://www.johndcook.com/blog/2008/09/28/theoretical-explanation-for-numerical-results/
