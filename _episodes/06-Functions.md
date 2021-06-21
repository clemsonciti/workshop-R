---
title: "Function"
teaching: 10
exercises: 0
questions:
- "How to write function in R?"
- "How can I use the function from packages"
objectives:
- "Define function"
- "Learn to create `nested` function"
- "Return value(s) from function"
- "Check argument conditions with `stopifnot()` function"
-keypoints:
- "Use `function` to define a new function in R"
- "Use parameter to pass value to function"
- "Load function into program using `source()`"
---

A function is a set of scripts organized together to carry out a specific task. Writing efficient functions is an important skill that can significantly improve the productivity of data scientists and data science solutions. In this guide, you will learn the basics of writing a function and the types of functions, which will enable you perform analytical tasks more efficiently.

## Using custom functions

There are several in-built functions in R that can be used to perform analytical tasks, for example: `mean, min, max, quantile,summary`.
Detail on `mean()` function below:

```r
mean(arg)
```

Using function mean with missing value
```r
v <- c(2,NA,4,NaN,6)
mean(v,na.rm=TRUE)
```


## Using User-Define a function with 1 arg(ument)
Syntax:

```r
f <- function(arg){
  do function with argument
}
```

Example:

```r
squareroot <- function(a){
  a^0.5
}
squareroot(49)
```
## Using User-Define a function with 2 or more arg(uments)
Syntax:

```r
f <- function(arg1,arg2){
  do function with arg1 & arg2
}
```

Example:

```r
Addtwo <- function(a,b){
  a+b
}
Addtwo(1,2)
```
## Return specific value from function
Syntax:
```r
f <- function(args){
  f1 <- do function with args
  return(f1)
}
```
For example:
```r
# Function to convert oF to oC
F2C <- function(temp){
   c <- ((temp - 32) * (5 / 9))
   return(c)
}
F2C(100)
```

## Return list of (more) values from function
Syntax:
```r
f <- function(args){
  do function with args
  out1 <- do1
  out2 <- do2  
  output <- list(out1=out1,out2=out2)
}
```

Example:
```r
sqsum <- function(a){
  sq <- a^0.5
  sumsq <- a+sq  
  output <- list(sq=sq, sumsq=sumsq)
}
sqsum(49)
```

## Nested function
In complex data science use cases, we may have to work on nested functions, which contain functions within a function.
For example: Given dataset `mtcars`. Find the mean of fuel consumption `mpg` for cars that having 4 cylinders `cyl`

```r
data(mtcars)
names(mtcars)

# Step 1: find the cars that having 4 cylinders:
ind1 <- mtcars$cyl==4
# Step 2: find the fuel consumption of all the cars having 4 cylinders:
ind2 <- mtcars$mpg[ind1]
# Step 3: compute the mean
mean(ind2)
```
All the 3 steps can be nested into one command line for experience user:
```r
mean(mtcars$mpg[mtcars$cyl==4])
```

## Defensive programming with `stopifnot()` function
Defensive programming encourages us to frequently check conditions and throw an error if something is wrong. 
For example:
```r
F2C <- function(temp){
   stopifnot(is.numeric(temp)==TRUE)
   c <- ((temp - 32) * (5 / 9))
   return(c)
}
F2C(100a)
F2C(100)
```

