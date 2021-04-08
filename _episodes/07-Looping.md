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

## Apply
- Most often used to apply function to row or column of matrix
- Not really faster than loop but simpler coding

```r
str(apply)
m <- matrix(1:12,3,4)
print(m)
apply(m,1,sum)
apply(m,2,sum)
```
