[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

"3.1 Something like the class size paradox appears if you survey children and ask how many children are in their family. Families with many children are more likely to appear in your sample, and families with no children have no chance to be in the sample.

Use the NSFG respondent variable `numkdhh` to construct the actual distribution for the number of children under 18 in the respondents' households.

Now compute the biased distribution we would see if we surveyed the children and asked them how many children under 18 (including themselves) are in their household.

Plot the actual and biased distributions, and compute their means."

```{python}
import matplotlib.pyplot as plt

resp = nsfg.ReadFemResp()

actual_pmf = resp['numkdhh'].value_counts().sort_index()/len(resp['numkdhh'])
print('PMF:',actual_pmf)
biased_pmf = (actual_pmf*[0,1,2,3,4,5])/sum(actual_pmf*[0,1,2,3,4,5])
print('Biased PMF:', biased_pmf)

plt.plot([0,1,2,3,4,5], actual_pmf, drawstyle = "steps-mid", label = "actual")
plt.plot([0,1,2,3,4,5], biased_pmf, drawstyle = "steps-mid", label = "biased")
plt.xlabel("Number of Children")
plt.ylabel("PMF")
plt.legend()
plt.show()

actual_mean = sum(actual_pmf*[0,1,2,3,4,5])
print('Actual Mean:', actual_mean)

biased_mean = sum(biased_pmf*[0,1,2,3,4,5])
print('Biased Mean:', biased_mean)
```
