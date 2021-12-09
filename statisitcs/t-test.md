# An introduction to t-tests

https://www.scribbr.com/statistics/t-test/

A t-test is a [statistical test](https://www.scribbr.com/statistics/statistical-tests/) that is used to compare the [means](https://www.scribbr.com/statistics/mean/) of two groups. It is often used in [hypothesis testing](https://www.scribbr.com/statistics/hypothesis-testing/) to determine whether a process or treatment actually has an effect on the population of interest, or whether two groups are different from one another.

## When to use a t-test

A t-test can only be used when comparing the means of two groups (a.k.a. pairwise comparison). If you want to compare more than two groups, or if you want to do multiple pairwise comparisons, use an[ ANOVA test](https://www.scribbr.com/statistics/one-way-anova/) or a post-hoc test.

The t-test is a [parametric test](https://www.scribbr.com/statistics/statistical-tests/#parametric) of difference, meaning that it makes the same assumptions about your data as other parametric tests. The t-test assumes your data:

1. are independent
2. are (approximately) normally distributed.
3. have a similar amount of [variance](https://www.scribbr.com/statistics/variance/) within each group being compared (a.k.a. homogeneity of variance)

If your data do not fit these assumptions, you can try a [nonparametric](https://www.scribbr.com/statistics/statistical-tests/#nonparametric) alternative to the t-test, such as the Wilcoxon Signed-Rank test for data with unequal variances.


## What type of t-test should I use?

When choosing a t-test, you will need to consider two things: whether the groups being compared come from a single population or two different populations, and whether you want to test the difference in a specific direction.

### One-sample, two-sample, or paired t-test?

* If the groups come from a single population (e.g. measuring before and after an experimental treatment), perform a  **paired t-test** .
* If the groups come from two different populations (e.g. two different species, or people from two separate cities), perform a  **two-sample t-test** (a.k.a.  **independent t-test** ).
* If there is one group being compared against a standard value (e.g. comparing the acidity of a liquid to a neutral pH of 7), perform a  **one-sample t-test** .

### One-tailed or two-tailed t-test?

* If you only care whether the two populations are different from one another, perform a  **two-tailed t-test** .
* If you want to know whether one population mean is greater than or less than the other, perform a **one-tailed t-test.**
