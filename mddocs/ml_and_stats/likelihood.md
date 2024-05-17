---
title: "Likelihood Maximization (Draft)"
description: "What is Likelihood? How can it be used? What problems can it help us solve?"

date: "05/17/2024"
categories:
  - Statistics
  - Likelihood
---

Let's assume you have some data. To analyze them we would most probably try to estimate the mean or the standard deviation. However we would be able to extract even more useful information about the data if we would be able to estimate the probability density function. 

Overall we want to estimate the $p(x|\theta)$, by finding the optimal values of $\theta$. If we have multiple candidate models, how can we decide what is the best one? This is what **likelihood** is used for. x

----
The likelihood expresses a way to determine how probable it is that the data came from a distribution with specific parameters.
----


- Normal Distribution: $p(x|\mu, \sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{1}{2\sigma^2}(x-\mu^2)}$
- Exponential Distribution: $p(x|\lambda) = \lambda e^{-\lambda}$

If we have the following data $x_1,x_2 \ldots x_n$ then the probability that they all came from a specific distribution with parameters $\theta$ is:

$$p(x|\theta) = \prod_{i=1}^n p(x_i|\theta)$$

The likelihood is a function of $\theta$ and by maximizing it we find the optimal values. Since the multiplication of all of those probabilities can cause problems in the computation (because of the representation of float numbers in a computer), we try to maximize the $logp(x|\theta)$ which will lead to the same value. It is denoted by $L(\theta)$

$$L(\theta) = logp(x|\theta) = \sum_{i=1}^{n} logp(x_i|theta)$$

## Applying the maximum likelihood estimation method

if we tried to maximize the likelihood estimation for the normal distribution we would get that this is possible.

- by maximizing for $\mu$: $\frac{dL}{d\mu} = 0$ then we would get that $\mu = \frac{1}{n} \sum_{i=1}^nx_i$
- by maximizing for $\sigma$ $\frac{dL}{d\sigma^2} = 0$ then we would get that $\sigma^2 = \frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^2$

for the exponential distribution:

$\frac{dL}{d\lambda} = 0$ then we get $\lambda = \frac{n}{\sum_{i=1}^n x_i} = \frac{1}{\bar{x}}$

for the bernoulli distribution where $p(x|\pi) = \pi^x(1-\pi)^{1-x_i}$ we would get:

$\frac{dL}{d\pi} = 0$ then we get $\pi = \frac{1}{n}\sum_{i=1}^n x_i$

## Maximum likelihood estimation using a mixture of distributions

$$p(x|\theta) = \sum_{k=1}^K w_k p_k(x|\theta_k)$$

e.g Gaussian Mixture Models