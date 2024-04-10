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

To remove all variables in the environment at the same time, use

```
rm(list=ls())
```

When using the RStudio IDE, code can be saved in scripts. To open a new script, click the icon with the green plus in the upper left corner, then select "R Script". All the code in the script can be executed at once by clicking "Source". Specific lines of code can be executed by selecting them and then clicking "Run".

Within scripts, comments can (and should!) be included by using `#`, as with Python

```
# This is a comment.
```

The fundamental data types in R are very similar to Python: numeric, integer, logical, character.

```
myNum <- 4.5
class(myNum) # numeric
is.numeric(myNum) # TRUE

myInt <- 8L # The L specifies that the 8 is an integer
class(myInt) # integer
is.integer(myInt) # TRUE

myLogical <- TRUE
class(myLogical) # logical
is.logical(myLogical) # TRUE

myStr <- "exampleString"
class(myStr) # character
is.character(myStr) # TRUE
```

All of the standard mathematical operations are available for `numeric` variables and literal numbers

```
a + 3
a - a
a * 4
12 / 4
```

## Data Structures

### Vectors

R has several data structures for storing sets of variables or values. For an ordered collection of values of the same type, use a vector

```
myVec <- c(1.5, 2.4, 3.4, 9.7, 6.3)
class(myVec) # numeric
```

The `c()` function combines different values into a vector. If you try to combine values or variables of different types, R will conver them all to the most general of those types (often `character`)

```
myOtherVec <- c("a", 7.8, 3L)
```

As with lists and tuples Python, vectors in R can be subset by providing one or more indices in square brackets

```
myVec[2]
myVec[c(2,4)]
```

### Matrices

Matrices are expansions of vectors in two dimensions. 

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

# Practice Exercises

## Exercise 1 - Learning about BREC Parks

1. Download the BREC parks dataset, "BREC_Park_Amenities_20240409.csv", available in this repository.
2. Create a new R script to analyze these data.
3. Read the data into R.
4. What type of R object is your dataset when it is first read in?
