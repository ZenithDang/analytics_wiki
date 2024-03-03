# Interpretation of P-Values

The P-Value is the probability of obtaining a test result at least as extreme as the result actually observed. In other words, this means the P-Value represents the likelihood of obtaining the results observed when the null hypothesis is true.

## Confidence Levels

Confidence levels describe the strictness of the statistical test and give an indication of how likely the test result is to occur. In general a confidence level is defined as $1- \alpha$ where $\alpha$ is the significance level. Common significance levels are 0.1, 0,05 and 0.01 which correspond to confidence levels of 90%, 95% and 99% respectively. Confidence and significance levels are usually set before a statistical test is conducted.

## P-Values and Statistical Tests

In a statistical test, a test statistic is calclated which has a corresponding P-Value. Using the P-Value and our chosen significance level, we are able to determine whether we reject or accept the null hypothesis. In general the rule to accept or reject the null are as follows:

- $P-Value \leq \alpha \rightarrow$ reject $H_0$
- $P-Value \geq \alpha \rightarrow$ accept $H_0$

For examples see:

- [Chi-SquareTest](Statistical%20Tests/Chi-Square%20Test.md)
- [T-Test](Statistical%20Tests/T-Test.md)
- [Fishers Test](Statistical%20Tests/Fishers%20Test.md)
- [ANOVA](Statistical%20Tests/ANOVA.md)
