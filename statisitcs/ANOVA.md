# An introduction to the one-way ANOVA

https://www.scribbr.com/statistics/one-way-anova/

ANOVA, which stands for Analysis of Variance, is a [statistical test](https://www.scribbr.com/statistics/statistical-tests/) used to analyze the difference between the [means](https://www.scribbr.com/statistics/mean/) of more than two groups.

A one-way ANOVA uses one [independent variable](https://www.scribbr.com/methodology/types-of-variables/), while a [two-way ANOVA](https://www.scribbr.com/statistics/two-way-anova/) uses two independent variables.


## When to use a one-way ANOVA

Use a one-way ANOVA when you have collected data about one **categorical independent variable** and one **quantitative dependent variable**. The independent variable should have at least three **levels** (i.e. at least three different groups or categories).

ANOVA tells you if the dependent variable changes according to the level of the independent variable. For example:

* Your independent variable is **social media use**, and you assign groups to **low**, **medium**, and **high** levels of social media use to find out if there is a difference in **hours of sleep per night**.
* Your independent variable is **brand of soda**, and you collect data on **Coke**, **Pepsi**, **Sprite**, and **Fanta** to find out if there is a difference in the **price per 100ml**.
* You independent variable is **type of fertilizer**, and you treat crop fields with mixtures **1**, **2** and **3** to find out if there is a difference in **crop yield**.

The [null hypothesis](https://www.scribbr.com/statistics/hypothesis-testing/) (H ~0~ ) of ANOVA is that there is no difference among group means. The alternate hypothesis (H ~a~ ) is that at least one group differs significantly from the overall mean of the dependent variable.

If you only want to compare two groups, use a [t-test](https://www.scribbr.com/statistics/t-test/) instead.

## How does an ANOVA test work?

ANOVA determines whether the groups created by the levels of the independent variable are statistically different by calculating whether the means of the treatment levels are different from the overall mean of the dependent variable.

If any of the group means is significantly different from the overall mean, then the null hypothesis is rejected.

ANOVA uses the F-test for[ statistical significance](https://www.scribbr.com/statistics/statistical-significance/). This allows for comparison of multiple means at once, because the error is calculated for the whole set of comparisons rather than for each individual two-way comparison (which would happen with a t-test).

The F-test compares the [variance](https://www.scribbr.com/statistics/variance/) in each group mean from the overall group variance. If the variance within groups is smaller than the variance between groups, the F-test will find a higher F-value, and therefore a higher likelihood that the difference observed is real and not due to chance.


## Assumptions of ANOVA

The assumptions of the ANOVA test are the same as the general assumptions for any parametric test:

1. **Independence of observations** : the data were collected using statistically-valid methods, and there are no hidden relationships among observations. If your data fail to meet this assumption because you have a [confounding variable](https://www.scribbr.com/methodology/confounding-variables/) that you need to control for statistically, use an ANOVA with blocking variables.
2. **Normally-distributed response variable** : The values of the dependent variable follow a [normal distribution](https://www.scribbr.com/statistics/normal-distribution/).
3. **Homogeneity of variance** : The variation within each group being compared is similar for every group. If the variances are different among the groups, then ANOVA probably isn’t the right fit for the data.
