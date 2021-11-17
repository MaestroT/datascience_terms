# The p-value explained

https://www.scribbr.com/statistics/p-value/

The  *p* -value is a number, calculated from a [statistical test](https://www.scribbr.com/statistics/statistical-tests/), that describes how likely you are to have found a particular set of observations if the null hypothesis were true.

*P* -values are used in [hypothesis testing](https://www.scribbr.com/statistics/hypothesis-testing/) to help decide whether to reject the null hypothesis. The smaller the  *p* -value, the more likely you are to reject the null hypothesis.

## What is a null hypothesis?

All statistical tests have a [null hypothesis. ](https://www.scribbr.com/statistics/hypothesis-testing/)For most tests, the null hypothesis is that there is no relationship between your variables of interest or that there is no difference among groups.

For example, in a two-tailed [ *t* -test](https://www.scribbr.com/statistics/t-test/), the null hypothesis is that the difference between two groups is zero.

## What exactly is a  *p* -value?

The  ***p***  **-value** , or probability value, tells you how likely it is that your data could have occurred under the null hypothesis. It does this by calculating the likelihood of your [**test statistic**](https://www.scribbr.com/statistics/test-statistic/), which is the number calculated by a statistical test using your data.

The  *p* -value tells you how often you would expect to see a test statistic as extreme or more extreme than the one calculated by your statistical test if the null hypothesis of that test was true. The  *p* -value gets smaller as the test statistic calculated from your data gets further away from the range of test statistics predicted by the null hypothesis.

The  *p* -value is a proportion: if your  *p* -value is 0.05, that means that 5% of the time you would see a test statistic at least as extreme as the one you found if the null hypothesis was true.

## How do you calculate the  *p* -value?

*P* -values are usually automatically calculated by your statistical program (R, SPSS, etc.).

You can also find tables for estimating the  *p* -value of your test statistic online. These tables show, based on the test statistic and **degrees of freedom** (number of observations minus number of independent variables) of your test, how [frequently ](https://www.scribbr.com/frequently-asked-questions/main-types-of-descriptive-statistics/)you would expect to see that test statistic under the null hypothesis.

The calculation of the  *p* -value depends on the statistical test you are using to test your hypothesis:

* Different statistical tests have different assumptions and generate different test statistics. You should choose the [statistical test](https://www.scribbr.com/statistics/statistical-tests/) that best fits your data and matches the effect or relationship you want to test.
* The number of [independent variables](https://www.scribbr.com/methodology/independent-and-dependent-variables/) you include in your test changes how large or small the test statistic needs to be to generate the same  *p* -value.


Example: Choosing a statistical test

If you are comparing only two different diets, then a two-sample  *t* -test is a good way to compare the groups. To compare three different diets, use an [ANOVA ](http://www.sthda.com/english/wiki/one-way-anova-test-in-r)instead – doing multiple pairwise comparisons will result in artificially low  *p* -values and lets you overestimate the significance of the difference between groups.



## Reporting  *p* -values

*P-* values of statistical tests are usually reported in the[ results section](https://www.scribbr.com/dissertation/results/) of a research paper, along with the key information needed for readers to put the  *p* -values in context – for example, correlation coefficient in a [linear regression](https://www.scribbr.com/statistics/simple-linear-regression/), or the average difference between treatment groups in a [ *t* -test](https://www.scribbr.com/statistics/t-test/).


## Caution when using  *p* -values

*P* -values are often interpreted as your risk of rejecting the null hypothesis of your test when the null hypothesis is actually true.

In reality, the risk of rejecting the null hypothesis is often higher than the  *p* -value, especially when looking at a single study or when using small sample sizes. This is because the smaller your frame of reference, the greater the chance that you stumble across a statistically significant pattern completely by accident.

*P* -values are also often interpreted as supporting or refuting the alternative hypothesis. This is not the case.** The  *p* -value can only tell you whether or not the null hypothesis is supported.** It cannot tell you whether your alternative hypothesis is true, or why.
