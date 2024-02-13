Analysis of variance essentially generalizes the [T-Test](T-Test.md) and allows us to compare two or more groups to see if their means are significantly different. In ANOVA the hypothesis are: 

- $H_0$ : The mean of all groups are equal. 
- $H_1$ : The mean of at least one group is different. 

**Note:** We are only looking at one way ANOVA for this page. 
## Example 

```{r}
df <- data.frame(
    education = sample(
        c("high school", "college", "graduate school"),
        300,
        TRUE,
        c(0.2, 0.5, 0.3)
        ),
    income = rnorm(300, 50000, 10000)
    )

anova(lm(income ~ education, data = df))
```
![](attachments/Pasted%20image%2020240213223717.png)

In this example, the P-Value is large indicating we cannot reject the null hypothesis. Thus, there is strong evidence to suggest the mean income of the different education groups are the same. 

Furthermore, we can test the assumptions of ANOVA by making a QQ Plot of the residuals. 

```{r}
aov(income ~ education, data = df)$residuals |> car::qqPlot()
```

![](attachments/Pasted%20image%2020240213224738.png)

From the above plot we can see the data is normal as most residuals lie on the line. We can also do a [Shapiro Test](Shapiro%20Test.md) on the residuals to test for normality. 

```{r}
aov(income ~ education, data = df)$residuals |> shapiro.test()
```
![](attachments/Pasted%20image%2020240213224846.png)

The large P-Value indicates that we cannot reject the null hypothesis, thus there is strong evidence suggesting the data is normally distributed. 

We can also test/inspect whether variance is equal between groups. We can use a box plot. 

```{r}
boxplot(income ~ education, data = df)
```

![](attachments/Pasted%20image%2020240213230203.png)

From the boxplot, the variances look roughly similar but not quite. We can use the [Levene Test](Levene%20Test.md) to confirm this. 

```{r}
car::leveneTest(income ~ education, data = df)
```
![](attachments/Pasted%20image%2020240213230413.png)

The small P-Value suggests we can reject the null hypothesis. Thus, there is strong evidence suggesting that the variances of income between education groups are not equal. Therefore, our Data does not meet the requirements for ANOVA. 
## Assumptions 

- Normal residuals. 
- Equality of variances between groups. 
- No outliers. 
- Data is randomly sampled from the population. 
- The dependant variable (the thing being called the mean of the groups) is a continuous variable and the independent variable is categorical (I.e. groups). 