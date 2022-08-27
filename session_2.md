Session 2
================
Dominic Bordelon, Research Data Librarian, University of Pittsburgh
Library System
June 21, 2022

``` r
library(tidyverse)
library(medicaldata)
library(readxl)
library(writexl)
```

# Session 2: Data wrangling

<figure>
<img src="assets/data_cowboy.png"
data-fig-alt="A green fuzzy monster in a cowboy hat and mustache, lassoing a group of unruly data tables while riding a blue fuzzy monster."
data-fig-align="center" alt="Artwork by @allison_horst" />
<figcaption aria-hidden="true">Artwork by @allison_horst</figcaption>
</figure>

## Agenda

1.  Pipes in R
2.  Selecting columns; filtering and sorting rows
3.  Creating new columns
4.  Grouping and summarizing
5.  Random sampling of rows
6.  Data cleaning: tidy data, missing values
7.  Exporting data from R

Most of what we are doing today is in the {dplyr} and {tidyr} packages.
These PDF cheat sheets are a handy reference:
[dplyr](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-transformation.pdf),
[tidyr](https://raw.githubusercontent.com/rstudio/cheatsheets/main/tidyr.pdf)

## Pipes in R

The **pipe** is an operator, written **`%>%`**, that enables us to pass
the output from one function, into another function. Consider:

``` r
my_values <- -1:-10    # -1 to -10, as a vector
my_values

# below i take the absolute value, then the square root, 
# then round to 3 decimal places, then calculate the mean
mean(round(sqrt(abs(my_values)), 3))

# with a pipe, this can be rewritten as:
my_values %>% 
  abs() %>% 
  sqrt() %>% 
  round(3) %>%
  mean()

# more readable, right?
```

The keyboard shortcut for `%>%` is **Ctrl+Shift+M** (Windows) or
**Cmd+Shift+M** (macOS).

You might also see a newer notation for the pipe, `|>`. It works the
same way:

``` r
my_values |>
  abs() |>
  sqrt() |>
  round(3) |>
  mean()
```

We’ll be using the first pipe, also called “the magrittr pipe” after the
package it comes from.

<figure>
<img src="assets/magrittr.png" data-fig-alt="magrittr logo"
data-fig-align="center" alt="magrittr logo" />
<figcaption aria-hidden="true">magrittr logo</figcaption>
</figure>

## Looking at data frames

`print()`, str()`,`View()`,`summary()\`

Get a histogram of a variable

``` r
ggplot(cvdrisk, aes(sbp)) + geom_histogram()
```

## Selecting columns; filtering and sorting rows

### `select()`: which columns?

### `filter()`: which rows?

<figure>
<img src="assets/dplyr_filter.jpg"
data-fig-alt="Cartoon showing three fuzzy monsters either selecting or crossing out rows of a data table. If the type of animal in the table is “otter” and the site is “bay”, a monster is drawing a purple rectangle around the row. If those conditions are not met, another monster is putting a line through the column indicating it will be excluded. Stylized text reads “dplyr::filter() - keep rows that satisfy your conditions.”"
data-fig-align="center" alt="Artwork by @allison_horst" />
<figcaption aria-hidden="true">Artwork by @allison_horst</figcaption>
</figure>

``` r
# comparisons: > >= < <= == !=


# check multiple values with the %in% operator, and a vector:

# BMI is between 25 and 30 (inclusive):
```

Multiple conditions can be combined with the symbols `&` (ampersand,
“AND”) and `|` (vertical pipe, “OR”).

### `arrange()`: in what order should the rows appear?

``` r
# sort by numAge:


# sort by numAge, descending (oldest first):

# sort by multiple columns:
```

## Exercise 1

1.  Using `filter()`, get patients aged 30+ whose systolic blood
    pressure is greater than 135. Store this set as an object called
    `high_bp`.

<!-- -->

2.  Sort `high_bp` according to numeric age and systolic blood pressure.

<!-- -->

3.  Why doesn’t the code below work? Can you fix it?

``` r
cvdrisk %>% 
  select(age, htn, treat, smoking, race, t2d, gender, bmi) %>% 
  filter(t2d == "Y") %>% 
  arrange(numAge)
```

## `mutate()`: Creating new columns

<figure>
<img src="assets/dplyr_mutate.png"
data-fig-alt="Cartoon of cute fuzzy monsters dressed up as different X-men characters, working together to add a new column to an existing data frame. Stylized title text reads “dplyr::mutate - add columns, keep existing.”"
data-fig-align="center" alt="Artwork by @allison_horst" />
<figcaption aria-hidden="true">Artwork by @allison_horst</figcaption>
</figure>

Example using the `smartpill` dataset:

## Grouping and summarizing

Often, our observations can be arranged into interesting *groups*,
typically based on a categorical variable (e.g., gender, race, age
group, treatment). Our next step is usually to *summarize* those groups:
how many observations in each group? What are the median and mean
values, standard deviation, etc.?

Available summarizing functions:

-   `n()`, `n_distinct()`
-   `mean()`, `median()`, `sum()`
-   `quantile()`, `min()`, `max()`, `IQR()`, `sd()`, `var()`

``` r
# or to apply the same summary function across() columns:
```

<figure>
<img src="assets/dplyr_across.png"
data-fig-alt="A cute round fuzzy monster with fairy wings and a wand, with a party hat on reading “mean”, bouncing across the top of a data table applying the function to each column. Stylized text reads: “dplyr::across() - use within mutate() or summarize() to apply function(s) to a selection of columns!” An example shows the use within summarize: summarize(across(where(is.numeric), mean))."
alt="Artwork by @allison_horst" />
<figcaption aria-hidden="true">Artwork by @allison_horst</figcaption>
</figure>

## `slice_sample()`: Random sampling of rows

meaning of “slice”

## Data cleaning: tidy data, missing values

When a dataset doesn’t have one observation per row and/or one variable
per column, we need to **reshape** it using `{tidyr}`.

<figure>
<img src="assets/tidydata_1.jpg"
data-fig-alt="Stylized text providing an overview of Tidy Data. The top reads “Tidy data is a standard way of mapping the meaning of a dataset to its structure. - Hadley Wickham.” On the left reads “In tidy data: each variable forms a column; each observation forms a row; each cell is a single measurement.” There is an example table on the lower right with columns ‘id’, ‘name’ and ‘color’ with observations for different cats, illustrating tidy data structure."
alt="Artwork by @allison_horst" />
<figcaption aria-hidden="true">Artwork by @allison_horst</figcaption>
</figure>

In `table2`, one column shows `type` (of measurement), either “cases” or
“population.”

``` r
View(table2)
```

We can use the information in `type` to make two new columns, `cases`
and `population`, which hold the value of `count`. We do this with
`pivot_wider()`:

In contrast, `table4a` has a column for each year; we would like to move
year information into its own column, and reduce the overall number of
columns to make the table “longer”—`pivot_longer()`.

## Exporting data from R

### Saving as CSV (readr)

### Saving as XLSX

### Saving as RDS and RData

.RDS and .RData are two file formats specific to R.

-   **RDS**, “R data structure” (I think), is for saving an R *object*
    (e.g., data frame) to disk. This file will be smaller than a CSV or
    XLSX and faster to load/save in R. This makes it a good choice for
    saving a dataset you’re working on.
-   **RData** is for saving your R *session* (Environment pane) to disk.
    Upon starting a session, this can be a faster way to restore your
    workspace than running your entire notebook again.

To save an object as RDS:

To load an RDS file into an R object:

``` r
# what does this loaded RDS look like?
```

To work with .RData files, the easiest way is to use the load/save icons
at top left of the Environment pane .

There is also an RStudio save-on-exit feature which preserves your
session (as a .RData), so that next time you open RStudio, you can pick
up where you left off. This is convenient, but requires diligent
notebook accounting.

<figure>
<img src="assets/config-rdata.png"
data-fig-alt="Cropped screenshot of RStudio&#39;s global option. The selection is titled Workspace. There is a checkbox labeled &quot;Restore .RData into workspace at startup&quot;. The box is unchecked. There is a drop-down menu reading &quot;Save workspace to .RData on exit:&quot;. The option &quot;Never&quot; is selected."
data-fig-align="center" alt="Tools &gt; Global Options… &gt; General" />
<figcaption aria-hidden="true">Tools &gt; Global Options… &gt;
General</figcaption>
</figure>

## Next steps

-   Problem Set 2
-   Next time: data visualization!