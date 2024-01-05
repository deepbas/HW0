Individual Homework 0
================

## Please submit your assignment to Gradescope by 10:00pm (Central) Monday, Jan 08.

You are currently in the GitHub repository (repo) for `hw0-username`.
The assignment prompt is shown below (i.e. in `README.Rmd`). You can
view this online in your homework 0 GitHub repository as a Markdown
file(`README.md`) or a pdf.

Please **use `hw0.Rmd` to complete this assignment**. Be sure to **knit
your file to PDF before your final push to GitHub**.

## Homework process

For help on the homework process, review

- [Assignments in Stat
  220](https://stat220-winter24.netlify.app/assignments.html) for
  content/formatting questions.

- [GitHub Guide for Students in Stat
  220](https://stat220-winter24.netlify.app/github.html) for Git and
  Github instructions.

When you are done with your homework, **don’t forget to push your
changes to ALL files back to GitHub**! (e.g. commit and push all files,
not just your final pdf)

------------------------------------------------------------------------

## Assignment prompt

``` r
# load necessary packages 
library(ggplot2)
library(dplyr)
library(gapminder)
library(babynames)
```

**Problem 1: Gapminder**

The `gapminder` package includes a data frame called `gapminder`,
containing information about different countries from 1952 to 2007. We
are interested in the year 2007 and we are going to save this in a new
data frame `gapminder_2007` below. We use data wrangling using code from
the `dplyr` package. We will learn about in detail later this later.

``` r
gapminder_2007 <- gapminder %>% 
  filter(year == 2007)
```

Run `View(gapminder_2007)` in your console to explore this data. An
alternative method for exploring a data frame is by using the
`glipmse()` function:

``` r
glimpse(gapminder_2007)
```

The function below plots the life expectancy Vs GDP per capita (in USD)
of all the countries in the `gapminder` dataset. You can see these
individual points color-coded by continent and the size of the points
correspond to the population of the country they correspond to. We will
dissect this function in detail in the coming weeks.

``` r
ggplot(data = gapminder_2007, 
       mapping = aes(x = gdpPercap, y = lifeExp, size = pop, color = continent)) +
  geom_point() +
  # Note: this was not required for this problem set:
  labs(x = "GDP per capita (in USD)", 
       y = "Life expectancy", 
       size = "Population", 
       color = "Continent", 
       title = "Gapminder data",
       subtitle = "2007 values")
```

1.  What country had the highest GDP per capita in 2007? Use the sorting
    arrows next to variable names in RStudio’s `View()` function.

*Answer:*

2.  Comment on the two biggest green circles that you see in the Figure
    1 above.

*Answer:*

**Problem 2: Babynames**

The `babynames` package provides data about the popularity of individual
baby names from the US Social Security Administration. Data includes all
names used at least 5 times in a year beginning in 1880.

In the code chunk below, we extract the data corresponding to `Aimee` or
`Sammy` from `babynames` dataset and store it in a new dataset
`babynames_Aimee_Sammy`.

``` r
babynames_Aimee_Sammy <- babynames %>%
  filter(name == "Aimee" | name == "Sammy")
```

1.  What do you see in the Figure 2 below? We will again learn the
    functions in detail later.

``` r
ggplot(babynames_Aimee_Sammy, aes(x=year, y=prop, col=sex)) +
  geom_line() +
  facet_wrap(~name) +
  labs(x = "Year", y = "Proportion", color = "Sex", title = "Comparison of Aimee and Sammy")
```

*Answer:*
