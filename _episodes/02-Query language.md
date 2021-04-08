---
title: "Basic of R"
teaching: 5
exercises: 0
questions:
- "how to initialize a variable"
- "how to do basic arithmetics"
- "how to get help"
objectives:
- "R built-in function"
keypoints:
- "Use RStudio to write and run R programs."
- "R has the usual arithmetic operators and mathematical functions."
- "Use `<-` to assign values to variables."
- "Use `ls()` to list the variables in a program."
- "Use `rm()` to delete objects in a program."
- "Use `install.packages()` to install packages (libraries)."
---

## Input to R
- In R console, the symbol `>` stands for `R prompt`.
- The `#` is for comment insert.
- To clean the existing environment, remove all memory in previous sessions:
```{r}
> rm(list=ls())
```
## Using R as calculator
When using R as a calculator, the order of operations is the same as you
would have learned back in school.

From highest to lowest precedence:

 * Parentheses: `(`, `)`
 * Exponents: `^` or `**`
 * Multiply: `*`
 * Divide: `/`
 * Add: `+`
 * Subtract: `-`
 * Other math functions: `sin, cos, log1(), log10(), exp`

~~~
> a <- (1+2)*3-4^5
> b <- sin(1)+log10(20)*exp(2)
~~~
{: .r}


## Compare in R
* `==`: equality
* `!=`: inequality 
* `<`& `<=`: less than & less than or equal to
* `>`& `>=`: more than & more than or equal to

~~~
> 1==1
~~~
{: .r}
