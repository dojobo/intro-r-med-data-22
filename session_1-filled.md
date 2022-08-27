Session 1
================
Dominic Bordelon, Research Data Librarian, University of Pittsburgh
Library System
June 14, 2022

# Session 1: **RStudio orientation and R basics**

Welcome!

## Agenda

1.  Course goals and structure; about the trainer
2.  What are R and RStudio? What can you do with them?
3.  RStudio Orientation
4.  Packages: what they are and installing them
5.  Import a spreadsheet as an R data frame
6.  Common data structures in R (data frames, vectors, lists)
7.  Objects and functions
8.  Next steps

## Course goals and structure

In *Intro to R for Data Analysis and Visualization*, using simple but
realistic examples, we will learn to:

1.  **orient** ourselves within the RStudio environment and with the
    syntax and general concepts of R
2.  **import**, **view**, **manipulate**, and **export data** in R
3.  perform basic **analysis** of tabular data
4.  create **visualizations** like scatter plots, histograms, and
    box-and-whisker plots
5.  create **documents** which intermix narrative hypertext, code, and
    plots for ease of communicating your research in a reproducible way.

We will meet for four sessions in Scaife 1101:

-   Tuesday, 6/14, 8:30–10am: RStudio orientation and R basics
-   Tuesday, 6/21, 8:30–10am: Data wrangling
-   Tuesday, 6/28, 8:30–10am: Data visualization and narration
-   Tuesday, 7/5, 8:30–10am: Statistical tests, modeling, and how to
    keep learning

Out-of-class work:

-   One problem set after each session, due 24 hours before next class
-   Maximum \~3 hours weekly

## About the trainer

**Dominic Bordelon**, Research Data Librarian  
University Library System – Digital Scholarship Services  
<dbordelon@pitt.edu>, https://pitt.libguides.com/dominicbordelon

Previously: background in humanities and libraries + self-taught coding
interest ➝ library IT and web development (\~5 yrs) ➝ Research Data
Librarian at Pitt since 11/2019

Support for various “data work”…

-   data management planning (esp. for grant proposals)
-   data cleaning, processing, analysis, visualization using tools like
    R and Python
-   project version control using Git and GitHub
-   understanding IT terms, how the internet works (HTTP, APIs), etc.,
    as it pertains to your research
-   data sharing and other Open Science topics

…via consultations ([book
here](https://pitt.libcal.com/appointments/research_data_librarian));
workshops for the Pitt community; on-request training

[Carpentries](https://carpentries.org/)[^1] Certified Instructor

Returning part-time undergrad in Ecology

## What are R and RStudio?

<img src="assets/Rlogo.svg" data-fig-alt="R logo"
data-fig-align="center" width="200" />

**R** is…

-   a tool for data analysis and visualization, especially in
    statistical and research contexts
-   a programming language
-   text-based command interface
-   biased towards tabular data and matrices (in practice)
-   free, open-source software (FOSS) stewarded by the nonprofit,
    Vienna-based R Foundation
-   full name: The R Project for Statistical Computing

<img src="assets/RStudio-Logo.svg" data-fig-alt="RStudio logo"
data-fig-align="center" width="400" />

**RStudio (Desktop)** is…

-   an “integrated development environment” for analysis and programming
    in R and Python
-   a graphical layer of software to facilitate our usage of R
-   RStudio is a Boston-based company, founded 2009, which makes both
    FOSS and commercial software[^2] and offers hosted services

### What can you do with R and RStudio?

Let’s follow the research data life cycle…

<figure>
<img src="assets/data-lifecycle.png"
data-fig-alt="A diagram of the research data life cycle. Steps: Plan, Acquire, Process, Analyze, Preserve, Share Results, Discover &amp; Re-Use"
data-fig-align="center" width="500"
alt="Research Data Lifecycle; source: Princeton Research Data Service" />
<figcaption aria-hidden="true">Research Data Lifecycle; source: <a
href="https://researchdata.princeton.edu/research-lifecycle-guide/research-lifecycle-guide">Princeton
Research Data Service</a></figcaption>
</figure>

#### Data collection from online sources

-   API == Application Programming Interface
    -   Many open data sources are accessible programmatically via HTTP
        APIs
    -   You can dynamically query the remote database and get the
        matching data back in a structured way, as opposed to needing to
        download many files.
    -   Some examples: Google Maps, Twitter, Fitbit, Census Reporter,
        COVID-19 Data Portal, NCI Genomic Data Commons
    -   Package: [httr](https://httr.r-lib.org/)
-   Web scraping
    -   Extracting information from web page HTML

    -   Package: [rvest](https://rvest.tidyverse.org/)

#### Data cleaning, processing, and reshaping

For example:

-   standardizing mixed column names, removing extra white space from
    cells
-   splitting and combining columns
-   detecting and handling missing values and outliers
-   reshaping tabular data

<img src="assets/pivot-longer.png" data-fig-align="center" />

Packages: [dplyr](https://dplyr.tidyverse.org/),
[tidyr](https://tidyr.tidyverse.org/)

#### Combining data from different sources

Table joins

Connect to databases

Packages: [dplyr](https://dplyr.tidyverse.org/),
[dbplyr](https://dbplyr.tidyverse.org/)

#### Types of data analysis and visualization

Statistical analysis (frequentist and Bayesian)

Machine Learning (e.g., TensorFlow)

Geocomputation, GIS:

-   Mapping (raster and vector)
-   Analysis and statistical modeling

Computational text analysis

Computational genomics:

-   working with genomic intervals
-   high-throughput RNA-seq and ChIP-seq analysis
-   DNA methylation analysis

High-performance computing (e.g., Hadoop)

#### Documents, slideshows, websites, books

-   [Literate
    programming](https://en.wikipedia.org/wiki/Literate_programming):
    mix narrative text, code, code outputs (e.g., viz or tables)
-   Hypertext: include images, links, embedded video, footnotes
-   Use
    ![\LaTeX](https://latex.codecogs.com/svg.latex?%5CLaTeX "\LaTeX")
    (esp. for math formulas)
    -   Inline mode example:[^3]
        ![H' = -\sum\_{i=1}^{R}p_i \ln p_i](https://latex.codecogs.com/svg.latex?H%27%20%3D%20-%5Csum_%7Bi%3D1%7D%5E%7BR%7Dp_i%20%5Cln%20p_i "H' = -\sum_{i=1}^{R}p_i \ln p_i")

    -   Display mode example:[^4]

![\theta = \frac{1}{(\frac{K_A}{\|L\|})^n + 1}](https://latex.codecogs.com/svg.latex?%5Ctheta%20%3D%20%5Cfrac%7B1%7D%7B%28%5Cfrac%7BK_A%7D%7B%7CL%7C%7D%29%5En%20%2B%201%7D "\theta = \frac{1}{(\frac{K_A}{|L|})^n + 1}")

-   Make inline citations and bibliography using Zotero and/or .bib
    files
-   One input file, many potential output formats (PDF, HTML, Word…)
-   Presentations can be PPTX, PDF, or browser-based ([demo
    here](https://quarto.org/docs/presentations/revealjs/demo/))
-   For many more examples check out the [RMarkdown
    gallery](https://rmarkdown.rstudio.com/gallery.html) or the [Quarto
    gallery](https://quarto.org/docs/gallery/)

#### Dashboards and other web apps

-   “Dashboard”: in-browser interface with viz of live, refreshing data
    (e.g., from a database), often with some interactivity
-   Packages: [Shiny](https://shiny.rstudio.com/),
    [plotly](https://plotly.com/r/)

## RStudio Orientation

### Panes

-   Bottom left: Console
    -   Run commands instantly in R
        ![\rightarrow](https://latex.codecogs.com/svg.latex?%5Crightarrow "\rightarrow")
        see command-line output
    -   Command history (press up arrow key)
-   Top left: Source/Editor
    -   Where you open files (tabbed)
    -   Write a script (multiple lines of R code), which you can *Run* (
        = RStudio sends each line of the script to the console pane)
    -   Can also be used to write documents in plain text or markdown,
        or *notebooks* in RMarkdown
-   Top right: Environment, History
    -   Global Environment = workspace of your current R session
-   Bottom right: Help, Working Directory

### RMarkdown/Quarto

-   This document is written in Quarto format, which is the most recent
    iteration of RMarkdown. A file written in RMarkdown is also called
    *an RMarkdown Notebook* or just *an R Notebook*.
-   Extends the popular
    [markdown](https://daringfireball.net/projects/markdown/) format
    (seen on Wikipedia and GitHub) by enabling the author to include
    executable code *chunks* like the one below
-   Switch between Source and Visual editors (buttons near top left of
    editor pane)

A code chunk:

### Configuration

-   Tools \> Global Options…
-   Many options can also be configured at project level
-   Keyboard shortcuts are very handy! Tools \> Keyboard Shortcuts Help

### Files and file types

-   [**R
    Projects**](https://support.rstudio.com/hc/en-us/articles/200526207-Using-RStudio-Projects)
    (.Rproj) are the suggested way of organizing your work in RStudio.
    Benefits include dedicated [command
    history](https://support.rstudio.com/hc/en-us/articles/200526217-Command-History-in-the-RStudio-IDE)
    and settings.
-   **R Notebooks** or RMarkdown documents (.Rmd) intermix R code and
    text formatted with markdown; the newest version are **Quarto
    documents** (.qmd)
-   **R scripts** (.R) are plain-text files that can be executed by R
    directly. However, because the file must be parseable, this means
    that the only permitted “natural language” is in code comments.

## 📦 Packages: what they are and installing them

In addition to R’s built-in functionality (“base R”), we can also
leverage work done by the community, released as **packages**. The
developer of a package loads it onto a public repository **CRAN** (the
Comprehensive R Archive Network). From CRAN, R users can install the
package onto their own computer.

Packages are typically built for a specific purpose or to collect a
specific set of functions. Here are some popular examples:

-   ggplot2: makes plots (using a “grammar of graphics”)
-   dplyr: filters, sorts, and modifies datasets
-   shiny: creates web applications, especially dashboards
-   stringr: has tools to help you work with character strings (text)
-   tmap: creates maps

### To install a package

-   Using your mouse:
    -   in the bottom right pane, click the Packages tab
    -   click the Install button at the top of the pane
    -   type the name of the package you want to install (example:
        `stringr`)
    -   click Install
-   Running code: `install.packages("stringr")` (replace `stringr` with
    the name of your desired package)

### To use a package

Once installed, a package needs to be activated before you can use it.

-   Using your mouse:
    -   in the bottom right pane, click the Packages tab
    -   find the name of the package you want to activate (by scrolling
        or searching in the top-right box), example: `stringr`
    -   click the check-box next to the package name
-   Running code: `library(stringr)`

You will need to reactivate the package every time you start a new R
session.

### Let’s install and attach (activate) tidyverse

“tidyverse” is a popular collection of packages–and we’re about to use
it in the next section, so let’s install and activate:

``` r
install.packages("tidyverse")
install.packages("readxl")
```

``` r
library(tidyverse)
library(readxl)
```

## Import a spreadsheet as an R data frame

Easiest is the Import Dataset feature in the Environment pane (top
right).

The Import Dataset feature generates code, which you can paste into a
code chunk, like the one below:

``` r
tg <- read_excel("data/tumorgrowth.xlsx", 
           sheet = "AnalysisData")

cvdr <- read_csv("data/genoData.csv")
```

    Rows: 59874 Columns: 17
    ── Column specification ────────────────────────────────────────────────────────
    Delimiter: ","
    chr (13): patientID, age, htn, treat, smoking, race, t2d, gender, rs10757278...
    dbl  (4): numAge, bmi, tchol, sbp

    ℹ Use `spec()` to retrieve the full column specification for this data.
    ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

This way, the file-loading step will be saved in your document, so that
you can easily recreate your session.

## Common data structures in R

### Data frames

A **data frame** is structured in rows (“observations”) and columns
(“variables”). This can also be called tabular data. Our spreadsheet
above is imported as a data frame.

Let’s use the `View()` and `str()` functions to examine the data frame:

``` r
View(tg)

str(tg)
```

    tibble [574 × 5] (S3: tbl_df/tbl/data.frame)
     $ Grp  : chr [1:574] "1.CTR" "1.CTR" "1.CTR" "1.CTR" ...
     $ Group: num [1:574] 1 1 1 1 1 1 1 1 1 1 ...
     $ ID   : num [1:574] 101 101 101 101 101 101 101 101 101 101 ...
     $ Day  : num [1:574] 0 3 4 5 6 7 10 11 12 13 ...
     $ Size : num [1:574] 41.8 85 114 162.3 178.3 ...

You can refer to one variable (column) in a data frame with the **`$`**
(dollar sign):

``` r
tg$Size
```

      [1]   41.8   85.0  114.0  162.3  178.3  325.0  623.7  648.4  835.9 1030.4
     [11] 1141.8 1499.9 1429.3 1609.3 1678.3 1564.0   79.4  110.3  201.3  255.3
     [21]  349.1  357.5  670.0  624.3  640.6  618.8  584.9  809.7 1249.7 1262.2
     [31] 1336.8 1563.7   44.8   67.5   55.8   82.8  106.8  309.5  355.9  554.8
     [41]  740.4 1012.1 1948.2 2405.7   67.7   92.4   77.7  107.4  147.1  226.1
     [51]  285.3  541.5  551.9  609.8 1230.5 1839.6 1964.2   54.7   61.1   75.3
     [61]  112.5  117.8  164.9  816.2  846.4 1403.6 1699.3 2162.8   60.0   74.2
     [71]   98.9  103.3  106.4  166.3  269.2  478.4  356.4  498.8  915.8 1086.6
     [81] 2125.1   46.8  162.6  264.5  253.1  419.3 1273.5 1712.0 2342.6   49.4
     [91]  123.2  286.5  484.9  584.5 1581.9 1930.6 2295.9   49.1   65.6   88.9
    [101]  135.4  171.9  177.3  388.0  466.7  557.0  455.5  624.1  995.2 1157.6
    [111] 1069.7 1194.4 1725.8 1524.9 1737.7 1998.3   60.6   75.7   75.8  158.7
    [121]  306.2  397.4  398.2  639.3  556.4  815.9  907.9 1104.2 1275.0 1290.9
    [131] 2046.7   41.5   41.8   43.2   46.0   48.7   66.5   82.2   94.1  162.7
    [141]  169.9  398.7  416.0  526.7  716.3  734.9 1938.5   46.8   46.4   48.8
    [151]   56.7  113.9  231.8  318.3  413.1  747.4  700.4 1374.8 1374.1 1668.4
    [161] 1598.4 1725.1   39.5   71.2   62.4   84.8   88.6  138.0  270.3  310.7
    [171]  385.5  552.5  468.9  766.6  896.0 1279.0 1582.3 1701.4   53.5   41.2
    [181]   52.2   61.6   77.1  102.8   85.9   70.3  105.2  129.9  291.3  315.4
    [191]  322.5  768.1 1108.6 1321.0 1624.3 1853.5   43.5   50.2   56.5   87.0
    [201]   53.5   38.5   69.1   46.3   66.5   62.4   83.6  102.6  100.9  163.0
    [211]  172.4  162.5  223.7  416.0  445.2   64.4   63.9   76.3   85.8  186.3
    [221]  291.9  381.9  469.5  590.2  782.9 1182.8 1194.7 1407.2 1677.7 1784.9
    [231]   47.5   48.6   75.1   77.7  128.0  123.5  167.1  144.4  294.6  318.0
    [241]  580.5  621.6  601.6 1066.5  981.1 1380.3 1507.9 1767.9 2269.3   71.7
    [251]  134.0  172.2  247.4  239.4  604.9  538.2  583.5  664.8  743.5 1054.9
    [261]  998.4  890.1 1203.9 1123.9 1302.3 1654.0 1697.6 2114.6   44.1  104.2
    [271]  129.3  304.9  533.2  732.5 1083.6 1141.7 1751.9 2058.7   42.1   98.7
    [281]   59.7   80.2   87.8  173.2  253.1  287.5  427.4  589.5  525.1  934.3
    [291] 1041.9  920.7 1003.3  920.7 1584.5 1734.4 1760.5 2362.4   42.5   49.8
    [301]   58.5   69.3   97.4  133.8  294.6  322.7  324.8  442.4  505.0  632.7
    [311]  594.8  603.7  646.5  649.3 1044.8 1219.9 1316.1 1714.0   56.9  129.6
    [321]  106.2  120.6  170.3  239.0  743.9  697.5  990.8 1066.4 1167.2 1958.9
    [331]   46.7   50.9   59.2  139.8  159.3  183.4  244.4  328.0  368.1  455.3
    [341]  397.6  519.8  463.5  650.5  979.3  761.1  853.0 1518.8 2157.4   51.2
    [351]   88.5  128.7  315.7  326.7  376.2  429.3  723.6 1051.3 1177.5 1297.6
    [361] 1254.5 1426.6 2159.6   44.0   84.1   80.1   66.8   90.0  147.7  334.2
    [371]  476.9  517.9  651.8  616.6 1108.4  955.3  909.4 1071.8  988.0 1970.2
    [381]   59.8   84.0  277.2  612.4  712.3 1055.3 1268.3  956.9  929.9   40.7
    [391]   63.5   55.9   89.1   98.7  137.7  303.3  410.4  514.4  565.4  611.3
    [401]  677.0  778.9  656.5  737.5  721.4  902.4  776.4  882.6  865.8 1065.0
    [411]   58.2   73.1   91.0   86.9  375.7  405.0  511.0  891.6 1022.3 1372.7
    [421] 1535.9 1748.5 1538.9 1684.1 1690.8 1764.8 1754.0 1964.6 2188.7   41.3
    [431]   63.4  102.6  130.0  286.2  372.3  440.0  490.0  511.4  719.9  832.3
    [441]  822.1  899.5 1096.0 1577.1 1904.1   53.5   60.9  117.0  122.7   47.7
    [451]  114.1   45.8   57.4   46.3  118.3  209.0  245.5  424.4  389.4  689.8
    [461]  624.1  731.3  811.3  882.4  898.8  887.2  814.5  779.7  828.9  588.6
    [471]  543.3   48.2   60.3   59.3   90.6   66.7  149.6  121.1  186.0  323.6
    [481]  332.2  609.0  467.4  548.0  768.8  802.1  766.2  657.1  619.2  810.7
    [491]   47.7   98.2   92.8  145.1  167.0  252.7  479.4  541.1  681.2  527.1
    [501]  685.7  673.3  833.1  672.7  651.5  785.3  972.4  786.5  976.6 1070.9
    [511] 1109.9   69.2   69.5  144.8  224.4  319.8  296.1  494.6 1227.7 1144.6
    [521] 1144.6 1685.4 1827.0 2343.0   43.9   58.5   45.6   77.9  224.7  183.7
    [531]  233.7  289.4  287.9  433.7  402.6  434.9  364.1  551.6  769.1  760.4
    [541]  760.4   59.3   92.6   92.5  169.3  218.1  257.2  236.2  243.7  229.2
    [551]  250.1  208.4  222.8  249.0  338.9  495.5  523.3  523.3   51.1   78.0
    [561]  107.4  128.0  167.3  219.8  375.6  645.9  691.4 1114.2 1050.4  940.6
    [571] 1057.0 1107.6 1694.2 1423.6

Data frames are the most typical structure we’ll encounter.

### Vectors

On a more basic level than a data frame, a **vector** is R’s way to
handle multiple items. We create a vector using the `c()` function. For
example, suppose I observe the measurements `41.8`, `85.0`, and `114.0`:

``` r
c(41.8, 85.0, 114.0)
```

    [1]  41.8  85.0 114.0

``` r
# we can write comments with the pound sign;
# these are ignored by R

# to save a vector as an object:
size <- c(41.8, 85.0, 114.0)
```

Vectors are designed to work efficiently with many repetitive or setwise
operations, for example, applying a mathematical operator or function to
every item in a vector. We also say these functions/operations are
**vectorized**.

``` r
size * 2
```

    [1]  83.6 170.0 228.0

``` r
sqrt(size)
```

    [1]  6.465292  9.219544 10.677078

A limitation of vectors is that every item must be of the same data type
(e.g., character or numeric). But they’re sort of R’s default data
structure. They’re also the foundation of data frames: each column is
actually a vector, which means we’ll be working with them a lot.

### Exercise 1

A handy function is `help()`, which queries R’s documentation system.
Most commonly, you’ll look up functions. You can search by running
`help(topic)` or `?topic`, e.g., `?sqrt`. Notice that the result will
appear in the Help pane.

1.  There is confusion among some R users what the “c” in the function
    `c()` stands for. Using the help system, what does `c()` do? What do
    you think “c” stands for?

<!-- -->

2.  Create a vector of arbitrary patient ages and store it as an object
    called `ages`.

<!-- -->

3.  What do you estimate is the mean age? Calculate it using `mean()`.

<!-- -->

4.  What is the mean value of the `Size` variable in `tg`? How about
    `numAge` in `cvdr`?

### Matrices

Vectors are one-dimensional. For 2+ dimensions, we need a **matrix**. We
won’t use them very much in this course, but they are available for you
to investigate further.

``` r
1:9     # the integer sequence 1 to 6, as a vector
```

    [1] 1 2 3 4 5 6 7 8 9

``` r
matrix(data = 1:9, nrow = 3, ncol = 3)
```

         [,1] [,2] [,3]
    [1,]    1    4    7
    [2,]    2    5    8
    [3,]    3    6    9

### Lists

Lists are collections of items; unlike vectors, they are potentially
heterogeneous. You can also give a name to each item in a list if
desired. Many specialized data structures are lists with special
attributes and functionality.

``` r
list(sex = c("F", "M"),
     group = c("Control", "1", "2", "3"),
     "cm",
     25:35)
```

    $sex
    [1] "F" "M"

    $group
    [1] "Control" "1"       "2"       "3"      

    [[3]]
    [1] "cm"

    [[4]]
     [1] 25 26 27 28 29 30 31 32 33 34 35

### Factors

A **factor** is a vector which represents a categorical variable, i.e.,
that there are only a finite number of possible values. Examples of
categorical variables:

-   assigned biological sex, gender
-   month, day of week, week number of year
-   shoe size, athletic weight class (but not: height, weight)

The possible values of a factor are its **levels**. Levels may be
**ordered** (e.g., month) or unordered (e.g., sex, eye color).

To create a factor, use the `factor()` function. R will automatically
determine the levels, but you can specify them, as well as whether they
are ordered.

``` r
factor(c("Control", "Group 1", "Group 2"))
```

    [1] Control Group 1 Group 2
    Levels: Control Group 1 Group 2

Sometimes your dataset might have categorical data coded numerically
(e.g., `1` for females and `2` for males), such that you will also want
to have a way to store human-readable **labels**.

``` r
factor(c(1, 2, 1, 1, 2, 1, 2, 2, 2, 1, 2, 1, 1),
       levels = c("1", "2"),
       labels = c("F", "M"))
```

     [1] F M F F M F M M M F M F F
    Levels: F M

## Objects and functions

When we give R a command, it usually returns an **object** of some kind.
We can usually see a representation of this object in the console when R
returns the object.

To store the object in memory, in order to view it more than once or
modify it, we will need to assign a name to the object. *(Note: saving
to memory ≠ saving to disk!)* We’ll use the **assignment operator**,
written **`<-`**, between our new object’s name and the function call.
For example:

``` r
c(41.8, 85.0, 114.0)      # creates a vector with three values
```

    [1]  41.8  85.0 114.0

``` r
size <- c(41.8, 85.0, 114.0)      # creates the vector and saves it to an object called "size"

# note the "size" object in your Environment tab!
size
```

    [1]  41.8  85.0 114.0

### Data types

On object’s data type determines what kinds of operations we can do on
the object. For example, numeric and character vectors have different
behaviors:

``` r
group <- c("Group 1", "Group 2", "Group 1", "Group 1")

size * 2
group * 2   # error!
```

To find out an object’s data type, you can see it listed in the
Environment tab (`chr`, `num`) or run the `typeof()` function.

### Functions

A function can have one or more **arguments**; for example, the `sqrt()`
function takes an `x` argument, which we could also write as `sqrt(x)`.
In the code chunk below, we use the `size` object for the `x` argument:

``` r
sqrt(size)
```

    [1]  6.465292  9.219544 10.677078

``` r
# R also supports "named arguments":
sqrt(x = size)
```

    [1]  6.465292  9.219544 10.677078

We say that a function **returns** its output (often an object);
`sqrt(16)` returns `4`.

You can also write your own functions, using **`function()`**. Here is a
function that raises `x` to the `y` power:

``` r
my_new_function <- function(x, y) {
  return(x^y)
}

my_new_function(2, 3)     #   == 2^3
```

    [1] 8

### Exercise 2

1.  Consider:

``` r
my_seq <- c(1, 2, 3)
my_seq <- c(my_seq, 4, 5)    # predict my_seq's value

my_seq <- c(my_seq, 6, c(7, 8))    # and here?
```

2.  Consider the factor in the code chunk below. Does `bases` have the
    value you expect? If not: what do you think is going on here?

``` r
bases <- factor(c("A", "C", "G", "A", "T", "G", "U", "C"), 
                levels=c("A", "C", "G", "T"))

bases
```

    [1] A    C    G    A    T    G    <NA> C   
    Levels: A C G T

3.  Write `bmi()` and `bmi_imperial()` functions. There is some template
    code below to get you started. (To calculate BMI: divide weight (kg)
    by height (m) squared. For Imperial units (lb/in), also multiply the
    result by 703.) Try to apply it with some numbers and see if it
    gives expected results.

``` r
bmi <- function(weight_kg, height_m) {
  
}

bmi_imperial <- function(weight_lb, height_in) {
  
}


test_weights <- c()
test_heights <- c()
bmi(test_weights, test_heights)
```

    NULL

## Wrapping up

Today we learned about:

-   R and RStudio orientation
-   Importing spreadsheets
-   Data structures: data frames, vectors, matrices, lists, factors
-   Object and functions

Expect Problem Set 1 later today, due 24 hrs before next session

Next time, we’ll do useful work with data frames!

[^1]: The Carpentries is a community which “builds global capacity in
    essential data and computational skills for conducting efficient,
    open, and reproducible research” through evidence-based instructor
    and mentor training and open learning materials
    ([link](https://carpentries.org/about/)). It is fiscally sponsored
    by Community Initiatives, a CA-based 501(c)(3) nonprofit.

[^2]: FOSS products: RStudio Desktop, RStudio Server, Shiny Server, and
    many R packages. Commercial products: RStudio Team, RStudio
    Workbench.

[^3]: Shannon Diversity Index,
    https://en.wikipedia.org/wiki/Diversity_index#Shannon_index

[^4]: the Hill equation,
    <https://en.wikipedia.org/wiki/Hill_equation_(biochemistry)>
