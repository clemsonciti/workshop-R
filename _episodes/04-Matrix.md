---
title: "Matrices & Data Frame"
teaching: 20
exercises: 0
questions:
- "How to define matrix in R?"
- "How to manipulate a data frame in R?"
objectives:
- "Working with Matrix"
- "Create data frame"
- "Import and export data frame"
keypoints:
- "Working with csv input data"
---

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

