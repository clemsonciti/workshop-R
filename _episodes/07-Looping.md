---
title: "Looping on the command line"
teaching: 10
exercises: 0
questions:
- "How to apply function over the list, matrix?"
objectives:
- "Learn apply, sapply, lapply function"
keypoints:
- "apply function"
---

There are functions in R that make looping easier:

- apply: apply function over margins of array
- lapply: looping over list and evaluate function on element
- sapply: similar to lapply, but simpler
- mapply: multivariate version of lapply
- tapply: apply function over subsets of vector

## apply

- Most often used to apply function to row or column of matrix
- Not really faster than loop but simpler coding

```r
str(apply)
m <- matrix(1:12,3,4)
print(m)
apply(m,1,sum)
apply(m,2,sum)
```

Similar functions for matrix:
```r
rowSums(m)
colSums(m)
rowMeans(m)
colMeans(m)
```

## lapply & sapply
`l`: long
`s`: short
lapply & sapply applies the FUN to each element of a list
```r
list1 <- list(l1 = seq(1,10),l2=20:29,l3=rnorm(4))
lapply(list1,mean)
sapply(list1,mean)
```


