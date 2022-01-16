---
title: "Matrices & Data Frame"
teaching: 20
exercises: 0
questions:
- "Vector in R"
- "How to define matrix in R?"
- "How to manipulate a data frame in R?"
- "How to read text/csv file"
objectives:
- "Working with Matrix"
- "Create data frame"
- "Import and export data frame"
- "Working with text/csv files"
keypoints:
- "Working with csv input data"
---

## Vector math

R can do a lot of mathematical operations on vectors:

```r
a <- 3:7
b <- 20:24
a+b
a>b
a>5
a*b
a/b
```

What if vector lenghts don't match?
```r
a<-1:5
b<-1:6
a
b
a+b
```

## Matrices
Vectors are one-dimensional rows of numbers; matrices are two-dimensional tables. Like vectors, all elements of a matrix must be of the same data type. 

Let's create a matrix of zeros:

```r
m <- matrix (0, nrow=3, ncol=4)
m
```
When creating a matrix, you will need to specify number of rows and columns. 

You can create a matrix from a vector:

```r
m <- matrix(1:12,nrow=3,ncol=4)
m <- matrix(1:12,3,4)
m
dim(m)
```
Another way to create a matricex from a vector:
```r
m <- 1:12
dim(m) <- c(3,4)
```

## Basic Matrix Math
```r
m1 <- matrix(1:9,nrow=3,ncol=3)
m2 <- matrix(rep(10,9),3,3)
m1
m2
m1+m2
m1*m2
m1 %*% m2
```

Some additional matrix functions:
```r
# Define a matrix
mr <- matrix(runif(9),3,3)
#Transpose a matrix
t(mr)
#Diagonal elements of a matrix
diag(mr)
#Determinant
det(mr)
#Inverse
solve(mr)
solve(mr) %*% mr
```

## Merging Matrices
Merging matrices by row and column using `rbind` and `cbind`:
```r
m 
m2 <- -1:-12
dim(m2) <- c(3,4)
m2
cbind(m,m2)
rbind(m,m2)
```
<!---
## Factors
Factors are used to represent categorical data
```r
m <- c("John","Mary","John","John","Jeff","Mary")
factor(m)
table(m)
```
-->

## Lists
In matrices and vectors, all elements belong to the same class. A collection of variables from different classes is called a list.

```r
str <- "Clemson"
a <- 5
b <- 4L
list1 <- list(str,a,b)
list1
```
Lists are very flexible. A vector, or a matrix, can be an element of a list:

```r
c <- 6i ^ (-3:3)
d <- 1:10 < 5
list2 <- list(str,a,b,c,d)
list2
```


## Subsetting

In order to extract the necessary information, subsetting is used.
In R, subsetting is represented by bracket: `[]`

```r
str <- c("a", "b","c","d")
str
# Find the subset with index 1 for str:
str[1]
# Find the subset with index 2:4 for str:
str[2:4]
```




**Subsetting with List**
```r
list1 <- list(l1=str,l2=4:6)
list1
# Use $ to call a variable name
list1$l1[3]
```

**Subsetting matrix**
```r
m <- matrix(1:12,nrow=3,ncol=4)
m
m[2,3]
```
Subsetting by row or column:
```r
m[2,]
m[,4]
```

**Subsetting `NA/NaN` value**
```r
a <- c(1:5,NaN,TRUE)
a
# Find the location of *NaN* value using `is.nan()` function
ind <- is.nan(a)
ind
# Subset with location of *NaN* value
a[ind]
a[is.nan(a)]
# Subset with location of `Not NaN` values using `!`
a[!ind]
```




## Data Frames
**Data frame is used to store tabular data, a table or 2-D array structure in which:**
- Each column contains values of one variable and
- Each row containts one set of value from each column

**Data Frame characteristics:**
- Column name should not be empty
- Row name should be unique
- Data can be numeric, integer, character, factor
- Each column contains same number of data items

```r
df <- data.frame(data=sample(12),title=LETTERS[sample(12)])
dim(df)
head(df)
names(df)
nrow(df)
ncol(df)
```
There are many available data frame in R, for example [`iris`](https://archive.ics.uci.edu/ml/datasets/iris) data set:
```r
data(iris)
```

## Names of Objects in Data Frames
Using `name()` function:
```r
names(iris)
# Change name
names(iris) <- c("a", "b", "c","d","e")
head(iris)

#Change name for particular columns:
names(iris)[4] <- "new_name"
```

## Getting data from Data Frames
Using columns or `$` to get the name of Data Frames;
```r
data(mtcars)
mpg1 <- mtcars$mpg
mpg2 <- mtcars[,1]
cylinder <- mtcars$cyl
```

## Reading and Writing Tables

**Reading Table**
Most popular syntax for reading table in R. Data can be read online by providing the link or read offline from the working directory

- `read.table`: read table in text format
- `read.csv`: read table in csv format
- `read.xlsx`: read table in excel format (require xlsx packages)
- `readLines`: read lines of a text file
- `source`: read R code

**Writing Table**
Similarly there are syntax for writing table:

- `write.table`: write table in text format
- `write.csv`: write table in csv format
- `write.xlsx`: write table in excel format (require xlsx packages)
- `writeLines`: write lines of a text file

In this example, I perform reading [online sale data](https://support.spatialkey.com/spatialkey-sample-csv-data/) and save the output to current working directory:
```r
# Read online csv data
saledata <- read.csv('https://support.spatialkey.com/wp-content/uploads/2021/02/Sacramentorealestatetransactions.csv')
dim(saledata)
names(saledata)

# Save output to csv file
write.csv(saledata,'SaleData.csv')
```

Here is another example using R to read a poem online and write poem to working directory
```r
# Reading poem
poem <- readLines("http://lib.ru/SHAKESPEARE/sonnets.txt")
poem[10:20]

# Writing poem
writeLines(poem[10:20],"Sonet1.txt")
```
