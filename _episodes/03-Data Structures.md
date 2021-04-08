---
title: "Data Structures"
teaching: 20
exercises: 0
questions:
- "Class of objects in R?"
- "Data Type in R?"
- "How many type of number in R?"
- "Missing values"
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


