---
title: "Data Structures"
teaching: 20
exercises: 0
questions:
- "Class of objects in R?"
- "Data Type in R?"
- "How many type of number in R?"
- "Missing values"
- "Subsetting"
objectives:
- "Identify 5 class of objects"
- "Working with List"
- "Type of number in R"
- "Replace number with subset"
keypoints:
- "Class of objects"
- "Subsetting" 
---

## Classes of objects
In R, there are 5 main classes of objects:
* characters a, b
* numeric: 2.3
* interger: 5 or 5L
* complex: 2+3i #consists of real and imaginary number
* logical: TRUE/FALSE

```r
str <- "string"
class(str)
a <- 5
class(a)
b <- 4L
class(b)
c <- 6i ^ (-3:3)
class(c)
d <- 1:10 < 5
class(d)
```

## List
A vector that containts objects from different class is call a `list`

```r
list1 <- list(str,a,b,c,d)
list1
```

## Number
* In R, the number is considered as numeric
```r
e <- 5
class(e)
```
* To get an integer, insert `L` as suffix
```r
f <- 5L
class(f)
```
* Special number: `Inf`: infinity
```r
g<-5/0
class(g)
```
* `NaN` (Not a Number) or `NA` (Not Applicable) are undefined values and sometimes refered as missing values:
```r
h <- 0/0
i <- NA
h
i
```

## Missing values
In order to test the missing values or bad values NaN, NA, Inf use some math operations:
* is.na() test NA value
* is.nan() test NaN value
* is.infinite() test Inf value
* NaN is NA but the reverse is false
```r
v <- c(TRUE, 6, 1/0,NA, NaN,-6/0)
v
is.na(v)
is.nan(v)
is.infinite(v)
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

** Subsetting with List**
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

** Subsetting `NA/NaN` value
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



