---
layout: post
title: Standard deviation in one pass and its impact on precision
subtitle: Lets do a small research of the optimization and its potential weaknesses
gh-repo: daattali/beautiful-jekyll
gh-badge: [star, fork, follow]
tags: [Stats, Python, R, Algorithms]
comments: true
---

{: .box-note}

## 1. Introduction
Lately during the interview I have reviewed an interesting problem about the optimization of the standard deviation calculation. Problem was well-known and was reviewed in an old Soviet book 
about [programmable calculators](https://www.xnumber.com/xnumber/russian_calcs.htm).  
In this post we will review the problem, its solution in Python and do a small study of the solution boundaries in terms of precision for different data. This post also could be a good illustration of multiple samples of billion data processing.

### 2. Problem description
Standard deviation of a probability distribution is defined as the square root of the variance σ².
σ = √(x²) - (x)² = √μ² - μ²
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
But here we need to loop over the data twice and the algorithm complexity will be O(n²). 
Is there a way to solve it in O(n)?

## 3. Solution
First lets rewrite the formula:  
$s_x^2 = \frac{1}{N} \sum_{i=1}^N (x_i - \bar{x})^2 = \frac{1}{N} \sum_{i=1}^N (x_i^2 - 2 \bar{x} x_i + \bar{x}^2)$
$= \frac{1}{N} \sum_{i=1}^N x_i^2 - \frac{2\bar{x}}{N} \sum_{i=1}^N x_i + \frac{N \bar{x}^2}{N}$
$=  \frac{1}{N} \sum_{i=1}^N x_i^2 - 2 \bar{x}^2 + \bar{x}^2 = \frac{1}{N} \sum_{i=1}^N x_i^2 - \bar{x}^2$

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

## 4. Studying precision for different data samples

Check precision for different data sizes (thousand, million, and billion records), 
distributions (Normal, Poisson, Binomial, Chi-Square, Exponential,F) and outliers (normal distribution, 5%, 10% ouliers (4SD+)). 

You may find experiment results in the table below. Numbers dipect absolute error 
between the std_dev_one_loop() and std_dev_two_loops() outputs.

  
| | Normal | Poisson | Binomial | Chi-Squared | Exponential | F | Normal+Outliers 5% | Normal+Outliers 10% |
|---|---|---|---|---|---|---|---|---|
| 1 thousand records | 0.0005 | 0.001084 | 0.000198 | 0.001524 | 0.0004965 | 0.000311 | 0.00064 | 0.00092 |
| 1 million records | 1.00E-06 | 1.00E-06 | 2.00E-07 | 1.00E-06 | 5.00E-07 | 3.00E-07 | 1.00E-06 | 2.00E-07 |
| 1 billion records | 1.00E-08* | 1.00E-08* | 1.00E-08* | 1.00E-08* | 1.00E-08* | 1.00E-08* | 1.00E-08* | 1.00E-08* |  

*precision could be higher, was not able to capture  

## 5. Results

Based on the results we may conclude that optimized method std_dev_one_loop() have reasonable precision +-10^3 on thousands of records,
high precision +-10^6 on million records and extremely high precision on billion records. 
Independently of the type of the distribution and outliers. Also in this post we have not studied the large numbers impact (our max outlier was 4SD from mean). That could be a major limitation for the described technique.


# 6. References

 https://www.strchr.com/standard_deviation_in_one_pass
 https://www.xnumber.com/xnumber/russian_calcs.htm
 https://mathworld.wolfram.com/StandardDeviation.html