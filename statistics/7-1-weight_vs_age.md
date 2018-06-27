[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

"7.1: Using data from the NSFG, make a scatter plot of birth weight versus mother’s age. Plot percentiles of birth weight versus mother’s age. Compute Pearson’s and Spearman’s correlations. How would you characterize the relationship between these variables?"

```{python}
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Solution goes here
#Spearman's
def SpearCorr(xs, ys):
    xs = pd.Series(xs)
    ys = pd.Series(ys)
    return xs.corr(ys, method = 'spearman')

l = SpearCorr(live['totalwgt_lb'], live['agepreg'])
print(l)   
#scatter plot

plt.scatter(live['agepreg'], live['totalwgt_lb'], alpha = 0.1)
plt.xlabel('agepreg')
plt.ylabel('totalwgt_lb')
plt.show()

#plot percentiles of birth weight v. mother's age
def binvspercentile(values):
    age = values.agepreg
    weight = values.totalwgt_lb
    bins = np.arange(10,48,3)
    indices = np.digitize(age, bins)
    groups = values.groupby(indices)
    
    mean_age = [group.agepreg.mean() for i, group in groups][1:-1]
    cdfs = [thinkstats2.Cdf(group.totalwgt_lb) for i, group in groups][1:-1]
    
    for percent in [75, 50, 25]:
        weights = [cdf.Percentile(percent) for cdf in cdfs]
        plt.plot(mean_age, weights, label = '%dth' % percent)
        
binvspercentile(live)

#Pearson's
def Corr(xs, ys):
    xs = np.asarray(xs)
    ys = np.asarray(ys)
    meanx = np.mean(xs)
    varx = np.var(xs)
    meany = np.mean(ys)
    vary = np.var(ys)
    
    cov = np.dot(xs-meanx, ys-meany)/len(xs)
    corr = cov/ np.sqrt(varx*vary)
    return corr

k = Corr(live['totalwgt_lb'], live['agepreg'])
print(k)
#0.0688339703541091

def SpearCorr(xs, ys):
    xs = pd.Series(xs)
    ys = pd.Series(ys)
    return xs.corr(ys, method = 'spearman')

l = SpearCorr(live['totalwgt_lb'], live['agepreg'])
print(l)   
#0.09461004109658228
```
The correlations are positive, but the magnitudes are small, indicating a weak positive correlation. Since the value of Pearson's coefficient is smaller than the value of the Spearman's coeffient, there could be some non-linear influencers.
