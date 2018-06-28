[Think Stats Chapter 9 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2010.html#toc90) (resampling)
"9.2: In Section 9.3, we simulated the null hypothesis by permutation; that is, we treated the observed values as if they represented the entire population, and randomly assigned the members of the population to the two groups.

An alternative is to use the sample to estimate the distribution for the population, then draw a random sample from that distribution. This process is called resampling. There are several ways to implement resampling, but one of the simplest is to draw a sample with replacement from the observed values, as in Section 9.10.

Write a class named `DiffMeansResample` that inherits from `DiffMeansPermute` and overrides `RunModel` to implement resampling, rather than permutation.

Use this model to test the differences in pregnancy length and birth weight. How much does the model affect the results?"

```{python}
class DiffMeansResample(DiffMeansPermute):
    
    def RunModel(self):
        g1 = np.random.choice(self.pool, self.n, replace = True)
        g2 = np.random.choice(self.pool, self.n, replace = True)
        return g1, g2

```
```{python}
import first
live, firsts, others = first.MakeFrames()
prglen = firsts.prglngth.values, others.prglngth.values
bweights = firsts.totalwgt_lb.dropna().values, others.totalwgt_lb.dropna().values

def DiffRS(data):
    data = firsts.prglngth.values, others.prglngth.values
    ht = DiffMeansResample(data)
    pvalue = ht.PValue(iters=500)
    return ("p-value:", pvalue)
    
print("Pregnancy length:", DiffRS(prglen))

print("Birth weights:", DiffRS(bweights))
```

The model doesn't seem to affect the results much.
