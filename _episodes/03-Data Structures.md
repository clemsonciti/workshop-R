---
title: "Data Structures"
teaching: 20
exercises: 0
questions:
- "Class of objects in R?"
- "Data Type in R?"
- "How many type of number in R?"
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

Typical object is a vector, that can be defined using function `c()`

```r
> str <- c("a","b","c")
> class(str)
> a <- rnorm(5)
> class(a)
> b <- 4:7
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
