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
