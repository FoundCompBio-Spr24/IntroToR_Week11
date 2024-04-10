# Introduction to R

## What is R?

- R is a language and environment for statistical computing and graphics.
- R provides a wide variety of statistical (linear and nonlinear modelling, classical statistical tests, time-series analysis, classification, clustering, …) and graphical techniques, and is highly extensible.
- R is an integrated suite of software facilities for data manipulation, calculation and graphical display.
- One of R’s strengths is the ease with which well-designed publication-quality plots can be produced.

Taken from: [The R Project for Statistical Computing](https://www.r-project.org/)

## Downloads

[The R Console](https://mirror.las.iastate.edu/CRAN/)

[The RStudio Integrated Development Environment (IDE)](https://posit.co/download/rstudio-desktop/)

## Additional Resources

[Introduction to R Tutorial](https://cran.r-project.org/doc/manuals/R-intro.pdf)

[Advanced R](https://adv-r.hadley.nz/)

## Syntax Fundamentals

The standard assignment operator in R is an arrow, `<-`

```
a <- 3.0
```

If using the RStudio IDE, variables (and their corresponding values) should appear in the upper right `Environment` panel. To display the values of variables in the console, use the `print()` function

```
print(a)
```

To remove a variable from the `Environment`, use the `rm()` function

```
rm(a)
```

## Tips and Tricks

- Tab completion
- Scrolling through command history
- Help

## Reading data from a file

For comma-delimited (`.csv`) data files, use `read.csv`

```
data <- read.csv("dataFile.csv")
```

For files with data delimited by whitespace, use `read.table`

```
data <- read.table("dataFile.txt")
```

