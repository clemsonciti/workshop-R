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

## Define a function with 1 arg(ument)
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
## Define a function with 2 or more arg(uments)
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

## Return value(s) from function
Syntax:
```r
f <- function(args){
  do function with args
  output <- list(out1=out1,out2=out2,out3=out3)
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

