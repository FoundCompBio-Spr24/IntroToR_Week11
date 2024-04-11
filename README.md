# Introduction to R

## What is R?

- R is a language and environment for statistical computing and graphics.
- R provides a wide variety of statistical (linear and nonlinear modelling, classical statistical tests, time-series analysis, classification, clustering, …) and graphical techniques, and is highly extensible.
- R is an integrated suite of software facilities for data manipulation, calculation and graphical display.
- One of R’s strengths is the ease with which well-designed publication-quality plots can be produced.

Taken from: [The R Project for Statistical Computing](https://www.r-project.org/)

## R versus Python

Both R and Python are flexible programming languages that can do a lot! As you work on your own research projects, you will likely find situations where one or the other is most helpful. Some of their relative strengths come from the goals behind their creation. Python is a general-purpose programming language that was designed to be more human readable and more fun than other general programming languages. R was designed by statisticians to specifically support data analysis, exploration, and visualization. Other relative strengths come from the history of their usage - in other words, how many people in different fields use those languages. Python tends to be much more widely used in genomics, for example, while R tends to be much more widely used in ecology. As such, scientists in each of those fields have developed extra packages and functionalities that are specific to those languages.

## Downloads

[The R Console](https://mirror.las.iastate.edu/CRAN/)

[The RStudio Integrated Development Environment (IDE)](https://posit.co/download/rstudio-desktop/)

## Additional Resources

[R for Data Science](https://r4ds.hadley.nz/)

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

The fundamental data types in R are very similar to Python: double, integer, logical, character. Both doubles and integers are considered numeric variables.

```
myNum <- 4.5
class(myNum) # numeric
is.double(myNum) # TRUE

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

All of the standard mathematical operations are available for numeric variables and values

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

### Matrices (and Arrays)

Matrices are expansions of vectors in two dimensions. All variables need to be of the same type. They can be created either by providing a vector of values and telling R how many rows and columns the matrix should have, as well as whether the values should be filled in along the rows or along the columns.

```
myMatrix <- matrix(c(1:9),nrow=3,ncol=3,byrow=FALSE)

myMatrix

#      [,1] [,2] [,3]
# [1,]    1    4    7
# [2,]    2    5    8
# [3,]    3    6    9
```

Matrices can also be created by taking separate vectors and binding them together as either rows or columns.

```
rowOne <- c(1,4,7)
rowTwo <- c(2,5,8)
rowThree <- c(3,6,9)

myMatrix <- rbind(rowOne,rowTwo,rowThree) # rbind() binds as rows
```

Individual values can be extracted from matrices by providing the row number and column number separated by a comma.

```
# The value in row two and column three
myMatrix[2,3]
```

Full rows or columns can be extracted (as vectors) from matrices by providing a single index with nothing on the other side of the comma.

```
rowTwo <- myMatrix[2,]
columnThree <- myMatrix[,3]

is.vector(columnThree) # TRUE
```

Matrices are particularly useful if you need to use any mathematical operations that are specifically defined for matrices (e.g., transpose, matrix products, etc.).

```
t(myMatrix) # transpose of the matrix

myMatrix %*% myMatrix
```

Arrays continue the expansion of vectors and matrices, but now for three or more dimensions.

```
myArray <- array(c(1:8),dim=c(2,2,2)) # two elements (rows, columns, etc.) in each of three dimensions

myArray[,,2]

#      [,1] [,2]
# [1,]    5    7
# [2,]    6    8
```

### Lists

Lists are similar to vectors, but more flexible. Importantly, they allow different data types to be stored together in one structure.

```
myList <- list(3L,"turtle",6.7)

myList

# [[1]]
# [1] 3

# [[2]]
# [1] "turtle"

# [[3]]
# [1] 6.7
```

Unlike vectors, the individual elements of a list are typically accesssed with double square brackets, `[[index]]`.

```
myList[[2]]

# [1] "turtle"
```

The different elements of a list can also be named. Some ways to construct lists will automatically assign names, but they can also be assigned or changed after a list is created.

```
names(myList) <- c("theIntegers","theWords","theDoubles")

myList

# $theIntegers
# [1] 3

# $theWords
# [1] "turtle"

# $theDoubles
# [1] 6.7
```

Once named, the elements of a list can be accessed (subset) using the `$` operator.

```
myList$theWords
```

Lists are particularly useful for storing heterogeneous data sets. Sometimes these consist of single values for each element in the list, but it is also common for the elements of a list to be other lists.

```
myList <- (c(3L,8L,10L,2L),
           c("turtle","chicken","duck"),
           rnorm(8))
```

## Tips and Tricks

- Tab completion
- Scrolling through command history
- Help

## Reading data from a file

As with both bash and Python, we always need to keep track of our working directory in R, when reading from or writing to files. If you're using RStudio, you can use the Files panel in the bottom right to navigate between different directories and files. You can also see your current working directory at any time by looking at the top line of the Console panel in the bottom left. To change working directories from the command line in R, you can use `setwd()`

```
# Changing my working directory
setwd("~/Desktop/Datasets/")
```

To read in data from comma-delimited (`.csv`) data files, use `read.csv()`. If your working directory is set to the same folder where the dataset is located, you can simply provide the name of the file.

```
data <- read.csv("dataFile.csv")
```

If the dataset is located somewhere other than your current working directory, you can provide a full path to the file

```
data <- read.csv("~/Downloads/dataFile.csv")
```

For files with data delimited by whitespace, use `read.table()`

```
data <- read.table("dataFile.txt")
```

# Practice Exercises

## Exercise 1 - Learning about BREC Parks

1. Download the BREC parks dataset, "BREC_Park_Amenities_20240409.csv", available in this repository. These data were originally downloaded from [Baton Rouge's Official Open Data Portal](https://data.brla.gov/)
2. Create a new R script to analyze these data.
3. Read the data into R.
4. What type of R object is your dataset when it is first read in?
5. Focusing on the acreage data, count how many parks are at least 5 acres in size.
6. Print out the names of those parks that are at least 5 acres.
7. What is the average acreage of all parks?
8. Which of the parks are classified as golf courses?
9. Which of the golf courses is biggest? Which is smallest?
