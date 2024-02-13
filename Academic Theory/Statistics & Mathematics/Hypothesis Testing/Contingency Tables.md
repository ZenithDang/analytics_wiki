A contingency table is a a table in a [matrix](https://en.wikipedia.org/wiki/Matrix_(mathematics)) format multivariate (as in multiple variables) frequency distributions of the variables. Generally, a contingency table will give you counts of the intersection between the levels in the variables being analysed. 

Contingency tables are often used in shaping data for statistical tests in R. They can also be useful in exploratory analysis. 

## 2 Dimensional Example

This can easily be shown using a 2 dimensional data set like the one generated below. 

```{r}
df <- data.frame(
    education = sample(
        c("high school", "college", "graduate school"),
        300,
        TRUE,
        c(0.2, 0.5, 0.3)
        ),
    occupation = sample(
        c("student", "unemployed", "employed", "self-employed"),
        300,
        TRUE,
        c(0.1, 0.2, 0.4, 0.3)
        )
    )
```

This dataset can then be turned into a contingency table like so. 

```{r}
table(df$education, df$occupation)
```

![](attachments/Pasted%20image%2020240210113633.png)

In this example, the rows and columns indicate the frequency distribution of the levels in each variable. For example, there are 54 employed college graduates, and 35 unemployed college graduates. 

## Higher Dimensions

In statistics we almost always are operating in higher dimensional areas, this is difficult to visualise in contingency tables in a human readable form. For example, if we introduced a third variable into our above example like below, we would get a separate table for each level in the third variable in the additional variable. 

```{r}
df <- data.frame(
    education = sample(
        c("high school", "college", "graduate school"),
        300,
        TRUE,
        c(0.2, 0.5, 0.3)
        ),
    occupation = sample(
        c("student", "unemployed", "employed", "self-employed"),
        300,
        TRUE,
        c(0.1, 0.2, 0.4, 0.3)
        ),
    ethinicity = sample(
        c("white", "black", "asian", "hispanic"),
        300,
        TRUE,
        c(0.3, 0.2, 0.3, 0.2)
        )
    )

table(df$education, df$occupation, df$ethinicity)
```

![](attachments/Pasted%20image%2020240210115049.png) 