[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

"5.1: In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters µ = 178 cm and σ = 7.7 cm for men, and µ = 163 cm and σ = 7.3 cm for women.

In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use `scipy.stats.norm.cdf`."

```{python}
import scipy.stats
mu = 178
sigma = 7.7

dist_h = scipy.stats.norm(loc=mu,scale=sigma)
dist.cdf(mu-sigma)

height_cm_max = (6*12 + 1)*2.54
height_cm_min = (5*12 + 10)*2.54

Percentage_male = dist_h.cdf(height_cm_max) - dist_h.cdf(height_cm_min)
Percentage_male
# 0.34274683763147457
```
