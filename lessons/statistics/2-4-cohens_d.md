[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

```python
def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d

# Returns False
first_are_heavier = firsts.totalwgt_lb.mean() > others.totalwgt_lb.mean()

# Both are very minuscule
d_totalwgt = CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)  # -0.088672927072602
d_prglngth = CohenEffectSize(firsts.prglngth, others.prglngth)  # 0.028879044654449883
```
