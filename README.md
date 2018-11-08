
# Poisson Distribution - Lab

## Introduction

In this lab, we'll put our knowledge of the Poisson Distribution to use to answer solve some sample real-world problems!

## Objectives

You will be able to:

* Understand and explain the Poisson Distribution and its use cases.


## Instructions

Solve the following sample problems by using python and your knowledge of the Poisson Distribution.

## Getting Started

Good Data Scientists plan ahead! Since you're going to be solving Poisson Distribution problems in this lab, it's probably a good idea to write a function that calculates Poisson Probability for us first. 

Recall that the Poisson Probability Formula is:

$$p(x) = \frac{\lambda^xe^{-x}}{x!}$$

Write a generalized that takes in the appropriate parameters and returns the Poisson Probability.

**_NOTE:_**  You can use `np.exp()` to quickly calculate $e$, and `math.factorial` (from the `math` library, not numpy) to calculate factorials. 

**_HINT:_** It's up to you whether or not you have your function calculate the value for lambda given $\mu$ and the interval, or whether you calculate lambda yourself beforehand and just pass it into the function. 


```python
import numpy as np
from math import factorial
```


```python
def poisson_probability(lambd=None, x=None, mu=None, interval=None):
    if lambd is None:
        lambd = mu*interval
    return (lambd**x)*(np.exp(-x))/factorial(x)
```

## Question 1

A fireman fights, on average, 4 fires per month. What is the probability that a fireman is called to two different fires this week?


```python
lambd_q1 = 1 # 1 fire per week -> mean in the given time interval
prob_q1a = poisson_probability(x=2, mu=4, interval=0.25) # 4 per month, interval = 0.25 of 1 month
prob_q1b = poisson_probability(lambd=1, x=2) # lambda = 1, x = 2
print(prob_q1a, prob_q1b)  # Expected Output:  0.06766764161830635
```

    0.06766764161830635 0.06766764161830635


## Question 2

A car salesman sells an average of 4 cars per week.  What is the probability they sell a car today?


```python
lambd_q2 = float(4/7)
prob_q2a = poisson_probability(lambd=lambd_q2, x=1) # lambda = 4/7 and x = 1
prob_q2b = poisson_probability(x=1, mu=4, interval=float(1/7)) # mu = 4 and interval is 1/7 of interval in mean
print(prob_q2a, prob_q2b)  # Expected Output: 0.21021682352653848
```

    0.21021682352653848 0.21021682352653848


## Question 3

A website makes an average of 50 sales per day.  What is the probability that they make 3 sales in an hour? 


```python
lambd_q3 = float(50/24)
prob_q3a = poisson_probability(lambd=lambd_q3, x=3)
prob_q3b = poisson_probability(x=3, mu=50, interval=float(1/24)) # hours is 1/24th of day
print(prob_q3a, prob_q3b)  # Expected Output: 0.07503114807560515
```

    0.07503114807560515 0.07503114807560511


## Question 4

A factory produces 250 cars per week (assume that the factory runs day and night all week with no down time). What is the probability that they produce 3 cars in the next hour?


```python
lambd_q4 = float(250/7/24)
prob_q4a = poisson_probability(lambd=lambd_q4, x=3)
prob_q4b = poisson_probability(x=3, mu=250, interval=float(1/7/24)) # week -> hour 
print(prob_q4a, prob_q4b)   # Expected Output: 0.02734371285554123
```

    0.02734371285554123 0.027343712855541224


## Question 5

The following table shows the number of houses sold by a realtor each week for the month of May. What is the probability that they sell 3 houses next week?

| Week | Houses Sold |
|:----:|:-----------:|
|   1  |      6      |
|   2  |      2      |
|   3  |      5      |
|   4  |      4      |


```python
mean_weekly_sales = np.mean([6, 2, 5, 4])
lambd_q5 = mean_weekly_sales
prob_q5a = poisson_probability(lambd=lambd_q5, x=3)
prob_q5b = poisson_probability(x=3, mu=mean_weekly_sales, interval=1)
print(mean_weekly_sales)
print(prob_q5a, prob_q5b)  # Expected Output: 0.6369892366961343
```

    4.25
    0.6369892366961343 0.6369892366961343


## Summary

In this lab, we got some practice making use of our knowledge of the Poisson Distribution to answer some real-world questions!
