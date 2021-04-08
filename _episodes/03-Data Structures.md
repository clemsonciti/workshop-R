---
title: "Data Structures"
teaching: 20
exercises: 0
questions:
- "Class of objects in R?"
- "Data Type in R?"
- "How many type of number in R?"
- "Missing values"
- "Vector in R"
objectives:
- "Identify 5 class of objects"
- "Working with List"
- "Type of number in R"
keypoints:
- "Read csv input"
---

## Classes of objects
In R, there are 5 main classes of objects:
* characters a, b
* numeric: 2.3
* interger: 5 or 5L
* complex: 2+3i #consists of real and imaginary number
* logical: TRUE/FALSE

```r
> str <- "string"
> class(str)
> a <- 5
> class(a)
> b <- 4L
> class(b)
> c <- 6i ^ (-3:3)
> class(c)
> d <- 1:10 < 5
> class(d)
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
