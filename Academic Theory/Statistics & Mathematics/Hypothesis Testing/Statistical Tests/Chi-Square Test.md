# Chi-Squared Test 

The [Chi-Squared Test](https://en.wikipedia.org/wiki/Chi-squared_test) is a [non-parametric](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3900058/) statistical test primarily used to compare whether two categorical variables (aka factors) are independent. In simpler terms:

- $H_0$ : the two categorical variables are independent from each other, i.e. not related.
- $H_1$ : the two categorical variables are not independent, and thus related.

Furthermore, being non parametric it assume no underlying distribution of the data.

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

Using R we can then perform a Chi-Square test to determine whether there is statistical evidence to suggest whether employment status and education level are independent. **Note:** the table function is used to shape the data into a [Contingency Tables](../Contingency%20Tables.md).

```{r}
chisq.test(table(df$education, df$occupation))
```

Doing this test we will get an output that looks like the following:

![](Attachments/Pasted%20image%2020240201200912.png)

In this case the P-Value is very large indicating we cannot reject the $H_0$ at the 10% level. Thus, there is strong statistical evidence indicating occupation and employment status are independent (i.e. not related).

## Assumptions/Requirements

- Large sample size (if small use [Fishers Test](Fishers%20Test.md) instead.)
- Variables are categorical (i.e. take on a finite set of values)
