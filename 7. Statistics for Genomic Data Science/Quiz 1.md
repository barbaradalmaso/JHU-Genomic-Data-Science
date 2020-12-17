# Module 1 Quiz

## Question 1
Reproducibility is defined informally as the ability to recompute data analytic results conditional on an observed data set and knowledge
of the statistical pipeline used to calculate them [Peng 2011, Science](https://science.sciencemag.org/content/334/6060/1226.abstract).
Replicability of a study is the chance that a new experiment targeting the same scientific question will produce a consistent result
[Asendorpf 2013 European Journal of Personality](https://maint.onlinelibrary.wiley.com).

Susan asks Joe for his data shared according to the data sharing plan discussed in the lectures. Which of the following are reasons the 
study may be reproducible, but not replicable?
* All the data and code are available but the codebook does not fully explain the experimental design and all protocols for patient recruitment. 
* Joe doesn't make the raw data accessible so Susan can't re-run his code.
* Susan only uses Python and Joe uses R so when she runs a new experiment, she will definitely get different results. 
* The code and data are available so the study is always replicable if it is reproducible. 

## Question 2
Put the following code chunk at the top of an R markdown document called
*test.Rmd* but set ```eval=TRUE```
``r
```{r setup, eval=FALSE}
knitr::opts_chunk$set(cache=TRUE)
```
``
