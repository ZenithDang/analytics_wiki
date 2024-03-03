# T-Test

The T-Test, is test mainly used to compare whether the average response of two populations are statistically difference. I.e. is the mean of two groups different from each other. Under this test in a two sided scenario the hypothesis are:

- $H_0$ : The difference in the two groups means are zero
- $H_1$ : The difference in the two groups means are non-zero

Furthermore, the test can be done one sided to determine if the difference in the groups means are positive are negative (from the perspective of one group).

## Example

In the below example we compare male and female height by generating data that follows a normal distribution. Given the data generation process it is known that male height has a greater mean than female height.

```{r}
male_height <- rnorm(100, 175,5)
female_height <- rnorm(100, 170, 5)

t.test(male_height, female_height)
```

![](attachments/Pasted%20image%2020240213214254.png)

From the two sided test we get a small P-Value indicating we can reject the null hypothesis. This means there is strong evidence the difference in mean height is not zero. We can now do a one sided test to determine if mean male height is lower than female height.

```{r}
t.test(male_height, female_height, alternative = "less")
```

![](attachments/Pasted%20image%2020240213214611.png)

A P-value of one gives strong evidence we can not reject the null hypothesis. I.e. strong evidence the difference in means is not less than 0 (so mean male height is not lower than mean female height). We can do the other side now.

```{r}
t.test(male_height, female_height, alternative = "greater")
```

![](attachments/Pasted%20image%2020240213214812.png)

A small P-Value gives strong evidence that we can reject the null hypothesis and accept the alternate hypothesis. There is strong evidence to suggest mean male height is greater than mean female height.

## Assumptions

- Mean of the two populations being compared follow a normal distribution.
- Equal variance or sample size, this is irrelevant when using [Welch&#39;s T-test.](https://en.wikipedia.org/wiki/Student%27s_t-test#Assumptions)
- The data of the two groups should be sampled independently.
