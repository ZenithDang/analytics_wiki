# Fishers Test 

Also called [Fishers Exact Test](https://en.wikipedia.org/wiki/Fisher%27s_exact_test) as the P-Value can be calculated to an exact figure unlike other statistical tests that use approximations at limits. This test offers an alternative to the [Chi-Square Test](Chi-Square%20Test.md) for when the sample size is small, though this test works for all sample sizes. The hypothesis for Fishers Test are as follows:

- $H_0$ : the two categorical variables are independent from each other, i.e. not related.
- $H_1$ : the two categorical variables are not independent, and thus related.

**Note:** this is the same as the Chi-Square Test, as such the below example is the same with a different function call for the statistical test.

## Example

To give a more solid example, let us say we are looking at a data set that contains a persons occupation status and their level of education. These are both categorical variables as they can only take a finite number of possible values. The data would look like as follows:

| Occupation | Education       |
| ---------- | --------------- |
| student    | High School     |
| unemployed | College         |
| Employed   | Graduate School |
| etc.       | etc.            |

The below R code generates a sample data frame.

```{r}
df <- data.frame(
    education = sample(
        c("high school", "college", "graduate school"),
        30,
        TRUE,
        c(0.2, 0.5, 0.3)
        ),
    occupation = sample(
        c("student", "unemployed", "employed", "self-employed"),
        30,
        TRUE,
        c(0.1, 0.2, 0.4, 0.3)
        )
    )
```

Using R we can then perform a Chi-Square test to determine whether there is statistical evidence to suggest whether employment status and education level are independent. **Note:** the table function is used to shape the data into a [Contingency Tables](../Contingency%20Tables.md).

```{r}
fisher.test(table(df$education, df$occupation))
```

Doing this test we will get an output that looks like the following:

![](Attachments/Pasted%20image%2020240202002140.png)

In this case the P-Value is large indicating we cannot reject the $H_0$ at the 10% level. Thus, there is strong statistical evidence indicating occupation and employment status are independent (i.e. not related).

## Assumptions/Requirements

- Variables are categorical (i.e. take on a finite set of values)
- Sampling or allocation are random
- Each observation (row) is [mutually exclusive](https://en.wikipedia.org/wiki/Mutual_exclusivity).
