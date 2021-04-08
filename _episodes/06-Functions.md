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

## Define a function
Syntax:

```r
f <- function(arguments){
  do function task
}
```

Example:

```r
squareroot <- function(a){
  a^0.5
}
squareroot(49)
```

## Return value(s) from function
Syntax:
```r
f <- function(arguments){
  do function task
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
