# R Statistics Exercises

To complete these exercises, create an R script file (.R file) or Quarto notebook (.qmd) file and write the code needed.

These exercises use data on Pokemon that can be imported into R directly from a URL:

```{r}
library(tidyverse)
pokemon <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/main/data/2025/2025-04-01/pokemon_df.csv')
```

Unfamiliar with Pokemon?  All you need to know to use this dataset is that each Pokemon is a fictional creature.  They have physical characteristics (height, weight, types, speed, colors, egg types, etc.) and they have skills that they can use to attack other Pokemon, defend themselves, and use other abilities in one-on-one battles.  HP (hit points) are how much damage they can take before they are defeated.  

Find information on the Pokemon variables at: https://github.com/rfordatascience/tidytuesday/blob/main/data/2025/2025-04-01/readme.md


## Exercise: Summary Statistics

Explore the hit points (hp) variable.  Visualize the variable and compute summary statistics.


## Exercise: Frequency Table

Investigate the type_1 and type_2 variables to see the frequency of each type.  

What is the most common combination?


## Exercise: Confidence Interval on Mean

What is the average attack points for a Pokemon?  Compute a 95% confidence interval on the mean.


## Exercise: Groups

What is the average hp for each type (type_1) of Pokemon?  Which type has the highest average?


## Exercise: Correlation

Are attack and defense points correlated?


## Exercise: t-test

Do fairy type (type 1) pokemon have a higher average hp than psychic (type 1) pokemon?

Hint: you'll need to subset the data to compute this.


## Exercise: Chi-squared test

The categorical variables in the dataset have a lot of categories.  Start by creating some categorical variables with fewer categories:

```{r}
# how big are they?
pokemon$size_cat <- ifelse(pokemon$height > 2.5 | pokemon$weight > 200, "large",
                           ifelse(pokemon$height > 1 | pokemon$weight > 100, "medium", "small"))

# how many types do they have?  1 or 2?
pokemon$n_types <- ifelse(is.na(pokemon$type_2), 1, 2)
```

Now, is there a relationship between size and the number of types a Pokemon has?



## Exercise: t-test

Do Pokemon with 2 types have stronger defenses that those with just 1 type?

Challenge: look up in the help/documentation how to compute a one-sided t-test and use that here instead of a two-sided one.  Choose the correct direction for the one-sided test.


## Exercise: Percentiles

What attack score does a Pokemon need to be in the top 5% in terms of attack?

What percentile is Pokemon Machoke in terms of attack strength?



## Exercise: ANOVA

Does Pokemon speed vary by their size category?

```{r}
# create size category variable
pokemon$size_cat <- ifelse(pokemon$height > 2.5 | pokemon$weight > 200, "large",
                           ifelse(pokemon$height > 1 | pokemon$weight > 100, "medium", "small"))
```


## Exercise: Correlation Matrix

Compute a correlation matrix for appropriate numeric variables in the dataset.

Challenge: visualize the correlation matrix


## Exercise: Linear Regression

Use a linear regression model to predict Pokemon hit points (hp).

Challenge: Use diagnostic plots to see if the assumptions about the distribution of residuals are met by your model.

Challenge: Make up stats for a new Pokemon and predict what the hp should be for your new creation.




