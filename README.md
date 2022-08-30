# An Intro to Data Analysis in R with medical data examples

A brief introductory course in data analysis in R (tidyverse) using various medical data

This course was given as 4 x 1.5-hour sessions in Summer 2022.

Basic concepts of R, simple quantitative analyses and visualizations, and data manipulation are emphasized here rather than statistical methods.

## How to use this repository

-   Lesson files are [Quarto](https://quarto.org/) documents (`.qmd` files)
-   Lesson files named `-filled.qmd` have code chunks filled completely, and can be used for self-study, as somewhat of an instructor script, or by students after class as a reference.
    -   Suggestion for a printed instructor script: in header YAML, add the [`docx` format](https://quarto.org/docs/output-formats/ms-word.html), and add `eval: false` as an [execution option](https://quarto.org/docs/computations/execution-options.html)
-   Remaining lesson files have empty chunks which are meant to be filled during class by instructor and students in a guided / live-coding format.
-   Problem sets provide a few after-class exercises and some additional information for students.
-   Lesson and problem set files are also rendered as `.md` files for viewing on GitHub

If you use this repository (e.g., in a classroom setting, or for self study), I would love to hear about it! (djb190 at pitt dot edu)

## Limitations/to-do

-   Instructor notes could be improved, especially communicating intent in specific sections, and/or more scripted narration
-   Solutions for problem sets are needed
-   Treatment of modeling could be improved
-   Problem set 3 is incomplete (needs more geom exercises)
-   Course outline needs updated to align with lesson 4

## Data sources

-   tumorgrowth.xlsx courtesy of [Dr. Jenna Carlson](https://publichealth.pitt.edu/home/directory/jenna-c-carlson)
-   [{medicaldata}](https://higgi13425.github.io/medicaldata/) R package
    -   smartpill
    -   messy_bp
-   [laderast](https://github.com/laderast)/[**cvdRiskData**](https://github.com/laderast/cvdRiskData)

## Contributing

Please feel free to open an Issue and/or fork and PR this repo!

## Acknowledgements

Thanks to Melissa Ratajeski, Jenna Carlson, Ravi Patel, Moira Stockton, and Forrest Shooster for sharing materials (especially datasets) and insights. Thanks to Hadley Wickham & Garret Grolemund for [R for Data Science](https://r4ds.had.co.nz/), and to the R and tidyverse development communities. Deep thanks to Moira Stockton for acting as a teaching assistant during sessions.

## References

-   Higgins P (2022). medicaldata: Data Package for Medical Datasets. <https://higgi13425.github.io/medicaldata/>, <https://github.com/higgi13425/medicaldata/>.
-   Wickham, Hadley, and Garrett Grolemund. *R for Data Science: Import, Tidy, Transform, Visualize, and Model Data*. Sebastopol, CA: O'Reilly, 2016. <https://r4ds.had.co.nz/index.html>.
-   Wickham H, Averick M, Bryan J, Chang W, McGowan LD, François R, Grolemund G, Hayes A, Henry L, Hester J, Kuhn M, Pedersen TL, Miller E, Bache SM, Müller K, Ooms J, Robinson D, Seidel DP, Spinu V, Takahashi K, Vaughan D, Wilke C, Woo K, Yutani H (2019). "Welcome to the tidyverse." *Journal of Open Source Software*, 4(43), 1686. <doi:10.21105/joss.01686>.
