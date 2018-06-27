[Think Stats Chapter 8 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77) (scoring)

"8.2: Suppose you draw a sample with size n=10 from an exponential distribution with λ=2. Simulate this experiment 1000 times and plot the sampling distribution of the estimate L. Compute the standard error of the estimate and the 90% confidence interval.

Repeat the experiment with a few different values of `n` and make a plot of standard error versus `n`."

```{python}
import numpy as np 
import matplotlib.pyplot as plt

n = 10
lam = 2
numexp = 1000

def SimExp(n, lam, numexp):
    means = []
    for _ in range(numexp):
        xs = np.random.exponential(1.0/lam, n)
        L = 1/ np.mean(xs)
        means.append(L)
    
    cdf = thinkstats2.Cdf(means)
    ci = cdf.Percentile(5), cdf.Percentile(95)
    stderr = RMSE(means, lam)
    
    values = [ci, stderr]
    return values
    
#plotting
n_list = [5, 10, 20, 30, 50, 60,100]
lam = 2
numexp = 1000

stderrs = [SimExp(k,lam,numexp)[1] for k in n_list]
plt.plot(n_list, stderrs)
