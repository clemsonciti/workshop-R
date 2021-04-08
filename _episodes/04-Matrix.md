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

## Vector
Typical object is a vector, that can be defined using function `c()` #c stands for combine

```r
str <- c("a","b","c")
a   <- c(4,5.6,20)
b   <- c("TRUE","FALSE")
```

A vector having different objects: `coercion`
```r
str1 <- c("a","b","c",5, 4.5)
str1
class(str1)
b1<- c(5, FALSE)
b1
class(b1)
```

## Explicit Coercion
Convert objects from one class to another, using `as.` function:
```r
a <- 0:5
class(a)
as.numeric(a)
as.logical(a)
as.character(a)
```
How about Nonsensical Coercion?
```r
str <- c("a","b","c")
class(str)
as.numeric(str)
as.logical(str)
as.character(str)
```

## Vectors Operation

```r
a <- 3:7
b <- 20:24
a+b
a>b
a>5
a*b
a/b
```

## Matrices
Matrics are vectors with dimension attribute. The dimension attribute is itself an integer vector of length 2 `(nrow, ncol)`

```r
m <- matrix(1:12,nrow=3,ncol=4)
m <- matrix(1:12,3,4)
m
dim(m)
```
Another way to create matrices
```r
m <- 1:12
dim(m) <- c(3,4)
```
Matrix Functions:
```r
# Define a matrix
mr <- matrix(runif(9),3,3)
#Transpose matrics
t(mr)
#Diagonal of matrics
diag(mr)
#Determinant
det(mr)
#Inverse
solve(mr)
```

## Merging Matrices
Merging matrices by row and column using `rbind` and `cbind`
```r
m2 <- letters[seq(from=1,to=12)]
dim(m2) <- c(3,4)
m2
cbind(m,m2)
rbind(m,m2)
```

## Matrices Operation
```r
m1 <- matrix(1:9,nrow=3,ncol=3)
m2 <- matrix(rep(10,9),3,3)
m1
m2
m1+m2
m1*m2
m1 %*% m2
```

## Factors
Factors are used to represent categorical data
```r
m <- c("John","Mary","John","John","Jeff","Mary")
factor(m)
table(m)
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
