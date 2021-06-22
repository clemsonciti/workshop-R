---
title: "Parallel Computing in R"
teaching: 20
exercises: 0
questions:
- "How to utilize multiple cores for R programming"
objectives:
- "Learn doParalel package"
- "Learn Parallel package"
keypoints:
- "doParallel()"
- "foreach()"
---

- The `doParallel` package is a "parallel backend" for the foreach package. It provides a mechanism needed to execute foreach loops in parallel.
- The `foreach` package must be used in order to execute code in parallel.
- The user must register a parallel backend to use, otherwise foreach will execute tasks sequentially, even when the %dopar% operator is used
- User must register a parallel backend to use. To register doParallel to be used with foreach, you must call the registerDoParallel function.

Example: 

Using some intensive computing function:
This function generates a square matrix of uniformly distributed random numbers, finds the corresponding (complex) eigenvalues and then selects the eigenvalue with the largest modulus. The dimensions of the matrix and the standard deviation of the random numbers are given as input parameters.
```r
max.eig <- function(N, sigma) {
     d <- matrix(rnorm(N**2, sd = sigma), nrow = N)
     E <- eigen(d)$values
     abs(E)[[1]]
 }
```

## Using foreach package
```r
foreach(i=1:4, .combine='c') %do% max.eig(i,1)
```

**Nested foreach**
```r
k=1
foreach(i=1:4) %:%
   foreach(j=1:4) %do%{
      max.eig(k,1)
      k=k+1
    }      
```

## Using `doParallel`
Check the number of available cpus:
```r
library(doParallel)
co <- detectCores()-1
cl <- makeCluster(co)
registerDoParallel(cl)
```

Apply `doParallel` to `foreach`
```r
system.time(foreach(i=1:200, .combine='c') %do% max.eig(i,1))
system.time(foreach(i=1:200, .combine='c') %dopar% max.eig(i,1))
stopCluster(cl)
```

## Using Parallel and parLapply
(Note: this does not work in Windows, mostly applicable to run in Palmetto)
Check number of available processing cpus:
```r
library(parallel)
co <- detectCores()-1
cl <- makecluster(co)
``` 

Apply `parLapply`
```r
#Load necessary packages on the cluster workers
clusterExport(cl, c('max.eig'))
system.time(foreach(i=1:200, .combine='c') %do% max.eig(i,1))
system.time(parLapply(cl, 1:200, function(z) max.eig(z,1)))
stopCluster(cl)
```

## Using built-in Parallel inside packages
Many packages have built-in paralle function. Here we use a bootstraping package: `boot`
```r
library(boot)
# function to obtain regression weights
bs <- function(formula, data, indices) {
  d <- data[indices,] # allows boot to select sample
  fit <- lm(formula, d)
  return(coef(fit))
}
# bootstrapping with 1000 replications
system.time(results <- boot(data=mtcars, statistic=bs,
                R=10000, formula=mpg~wt+disp))

system.time(results <- boot(data=mtcars, statistic=bs,
                R=10000, formula=mpg~wt+disp,
                parallel = "snow",ncpus=2))
```

