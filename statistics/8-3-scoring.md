[Think Stats Chapter 8 Exercise 3](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77)

"8.3: In games like hockey and soccer, the time between goals is roughly exponential. So you could estimate a team’s goal-scoring rate by observing the number of goals they score in a game. This estimation process is a little different from sampling the time between goals, so let’s see how it works.

Write a function that takes a goal-scoring rate, `lam`, in goals per game, and simulates a game by generating the time between goals until the total time exceeds 1 game, then returns the number of goals scored.

Write another function that simulates many games, stores the estimates of `lam`, then computes their mean error and RMSE.

Is this way of making an estimate biased?"

```{python}
# Solution goes here
import numpy as np

def gameEstimate(lam):
    t = 0
    goals = 0
    while t < 1:
        time_between_goals = random.expovariate(lam)
        t += time_between_goals
        if t < 1:
            goals += 1
    return goals


def manyGames(lam, iters):
    goals = []
    for _ in range(iters):
        goal = gameEstimate(lam)
        goals.append(goal)
    
    e2 = [(goal - lam)**2 for goal in goals]
    RMSE = np.sqrt(np.mean(e2))
    
    errors = [goal - lam for goal in goals]
    MeanError = np.mean(errors)
    
    print(RMSE, MeanError) 
```
This is unbiased, as the mean error decreases with increased iterations.
