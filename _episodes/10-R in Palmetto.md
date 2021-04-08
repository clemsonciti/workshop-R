---
title: "R in Palmetto"
teaching: 10
exercises: 0
questions:
- "How to R in Palmetto"
objectives:
- "Learn how to run R in Palmetto"
- "Learn how to install package in R in Palmetto"
keypoints:
- "Rscript"
- "R CMD BATCH"
---
Login to your Palmetto account [Palmetto login](https://www.palmetto.clemson.edu/palmetto/basic/login/)

- Request a compute node:
```bash
$ qsub -I -l select=1:ncpus=4:mem=32gb:interconnect=fdr,walltime=72:00:00
```

Load R module
$ module load r/3.6.0-gcc/8.3.1
Open R and run in Interactive mode:
$ R
> install.packages("doParallel")
Run R in batch mode
$ Rscript a.R
$ R CMD BATCH a.R # Will write separate output file
