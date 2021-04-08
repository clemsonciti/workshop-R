---
title: "Profiling the code"
teaching: 10
exercises: 0
questions:
- "How to get the computed time for a chunk of code?"
- "How to profile the R code"
objectives:
- "Learn system.time() function"
- "Learn Rprof() function"
keypoints:
- "system.time()"
- "Rprof()"
---

## Function Dates of system
```r
today_date <- Sys.Date()
print(today_date)
date1 <- as.Date("2017-12-02")
print(date1)
#different between date
print(today_date-date1)

time_now <- Sys.time()
print(time_now)
```

## Computation time for a chunk of code
- Examine how much time is spent in programming's parts.
- Useful for optimization your code with parallel computation
```r
system.time(runif(300^3)*3)
```

```r
system.time(Sys.sleep(20))
```
user: time charged to the CPU for this expr elapsed: "wall clock" time

## Profiler
`system.time()` allows to test certain functions or code blocks In order to know all functions, Profiler is used `Rprof()` function
