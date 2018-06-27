[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

"6.1": Compute the median, mean, skewness and Pearson’s skewness of the resulting sample. What fraction of households report a taxable income below the mean? How do the results depend on the assumed upper bound?

```{python}
#median
median = cdf.Value(0.5)
median 
#mean
mean = np.mean(sample)
mean

#skewness

def Skewness(xs):
    mean = sum(x for x in xs) / len(xs)
    var = (sum((x - mean)**2 for x in xs)/ len(xs))
    std = math.sqrt(var)
    return (sum((x-mean)**3 for x in xs)/ len(xs))/std**3

Skewness(sample)
#4.949920244429583

#Pearson's skewness

def PearsonsSkewness(xs):
    median = thinkstats2.Cdf(xs).Value(0.5)
    mean = np.mean(xs)
    var = (sum((x - mean)**2 for x in xs)/ len(xs))
    std = math.sqrt(var)
    gp = 3*(mean - median)/ std
    return gp

PearsonsSkewness(sample)
# 0.7361258019141741

#Income below mean
cdf.Prob(np.mean(sample))
#0.660005879566872
```
As the income cap is increased, the skewness of the sample increases.

               
               


