[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

"2.4 Using the variable `totalwgt_lb`, investigate whether first babies are lighter or heavier than others. Compute Cohen’s effect size to quantify the difference between the groups.  How does it compare to the difference in pregnancy length?"

```{python}
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

first_wgtlb = live[live.pregordr == 1]['totalwgt_lb']
others_wgtlb = live[live.pregordr != 1]['totalwgt_lb']
# firsts.totalwgt_lb.mean(), others.totalwgt_lb.mean()
# Out: (7.201094430437772, 7.325855614973262)

def Cohen_D(group1, group2):
    mean1 = group1.mean()
    mean2 = group2.mean()
    var1 = group1.var()
    var2 = group2.var()
    size1 = len(group1)
    size2 = len(group2)
    
    d_num = mean1 - mean2
    d_den = np.sqrt((size1*var1 + size2*var2)/(size1 + size2))
    
    d = d_num/d_den
                                 
    return d
    
print(Cohen_D(first_wgtlb, others_wgtlb))
# Out: -0.088672927072602
```
The Cohen's effect size for weight is ~-0.0887, which is around 3x greater than the Cohen's d (0.0289) for pregnancy length. However, the effect size is still quite small, which means that the difference between the two means is less than 1/10 of standard deviation.
