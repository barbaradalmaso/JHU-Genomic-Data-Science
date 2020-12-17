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
```
{r setup, eval=FALSE}
knitr::opts_chunk$set(cache=TRUE)
```
Then create the following code chunks
```
{r }
x = rnorm(10)
plot(x,pch=19,col="dodgerblue")
```
```
{r }
y = rbinom(20,size=1,prob=0.5)
table(y)
```
* The plot and table are random the first time you knit the document. They are identical the second time you knit the document. After removing the folders ```test_cache``` and ```test_files``` they generate new random versions.
* The table is random each time you knit the document, but the plot is always the same after you knit it the first time.
* The plot and table are random the first time you knit the document. They are identical the second time you knit the document. After removing the folders ```test_cache``` and ```test_files``` are still identical.
* The plot and table are random every time you kint the document, except for the last time.

## Question 3
Create a ```summarizedExperiment``` object with the following code
```r
library(Biobase)
library(GenomicRanges)
data(sample.ExpressionSet, package = "Biobase")
se = makeSummarizedExperimentFromExpressionSet(sample.ExpressionSet)
```
Look up the help files for ```summarizedExperiment``` with the code ``?summarizedExperiment.`` How do you access the genomic data for this object? How do you access the phenotype table? How do you access the feature data? What is the unique additional information provided by 
```rowRanges(se)```?
* Get the genomic table with ```assay(se)```, get the phenotype table with 
```colData(se)```, get the feature data with ```rowData(se)```.
```rowRanges(se)``` gives information on the genomic location and structure of the measured features.
* Get the genomic table with ```assay(se)```,get the phenotype table with 
```colData(se)```, get the feature data with ```rowRanges(se)```. 
```rowRanges(se)``` gives the range of possible values for the expression data.
* Get the genomic table with <code>assay(se)</code>, get the phenotype table with <code>pData(se)</code>, get the feature data with <code>rowData(se)</code>. <code>rowRanges(se)</code> gives information on the genomic location and structure of the measured features.
* Get the genomic table with ```assay(se)```, get the phenotype table with 
```colData(se)```, get the feature data with ```rowData(se)```. ```rowRanges(se)``` gives the range of possible values for the expression data.

## Question 4
Suppose that you have measured ChIP-Seq data from 10 healthy individuals and 10 metastatic cancer patients. For each individual you split the sample into two identical sub-samples and perform the ChIP-Seq experiment on each sub-sample. How can you measure (a) biological variability, (b) technical variability and (c) phenotype variability.
* (a) By looking at variation across samples from 10 different healthy individuals 

  (b) By looking at variability between the measurements on the two sub-samples from the same sample and 

  (c) by comparing the average measurements on the healthy individuals to the measurements on the individuals with cancer. 
* (a)  By looking at variation across samples from 10 different individuals with cancer 

  (b) By comparing the average variability in the cancer and normal individuals 

  (c) By comparing the average measurements on the healthy individuals to the measurements on the individuals with cancer.
* (a) By looking at variation across replicate sub-samples within the normal individuals 

  (b) By looking at variation across samples from 10 different healthy individuals 

  (c) By comparing the average measurements on the healthy individuals to the measurements on the individuals with cancer.
*  (a) & (b) By looking at variation across samples from 10 different healthy individuals. 

  (c) by comparing the average measurements on the healthy individuals to the measurements on the individuals with cancer. 

## Question 5
Load the Bottomly and the Bodymap data sets with the following code:
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bottomly_eset.RData")
load(file=con)
close(con)
bot = bottomly.eset
pdata_bot=pData(bot)

con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bodymap_eset.RData")
load(file=con)
close(con)
bm = bodymap.eset
pdata_bm=pData(bm)
```
Just considering the phenotype data what are some reasons that the Bottomly data set is likely a better experimental design than the Bodymap data? Imagine the question of interest in the Bottomly data is to compare strains and in the Bodymap data it is to compare tissues.
* The Bodymap data has measured more levels of the outcome of interest (tissues) than the Bottomly data has measured (strains).
* The Bottomly data set does not measure the age of the mice.
* Most of the tissues in the Bodymap data have a consistent number of technical replicates (2).
* The number of technical replicates in the Bodymap data varies, but the number in the Bottomly data is consistent.

## Question 6
What are some reasons why this plot is not useful for comparing the number of technical replicates by tissue (you may need to install the plotrix package).
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bodymap_eset.RData")
load(file=con)
close(con)
bm = bodymap.eset
pdata_bm=pData(bm)

library(plotrix)
pie3D(pdata_bm$num.tech.reps,labels=pdata_bm$tissue.type)
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archive/unnamed-chunk-5-1.png)
* The plot uses rainbow colors which are hard for color blind individuals to see. 
* Humans are much worse at comparing angles than comparing position or length.
* The plot would be much easier to see if the pie chart were rotated by 90 degrees from its current position. 
* The data could much more easily be shown as a heatmap. 

## Question 7
Load the Bottomly data:
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bodymap_eset.RData")
load(file=con)
close(con)
bm = bodymap.eset
edata = exprs(bm)
```
Which of the following code chunks will make a heatmap of the 500 most highly expressed genes (as defined by total count), without re-ordering due to clustering? Are the highly expressed samples next to each other in sample order?
* The highly expressed samples are next to each other.
```r
row_sums = rowSums(edata)
index = which(rank(-row_sums) < 500 )
heatmap(edata[index,],Rowv=NA)
```
* The highly expressed samples are next to each other.
```r
row_sums = rowSums(edata)
index = which(rank(-row_sums) < 500 )
heatmap(edata[index,],Rowv=NA,Colv=NA)
```
* The highly expressed samples are not next to each other.
```r
row_sums = rowSums(edata)
index = which(rank(-row_sums) < 500 )
heatmap(edata[index,],Rowv=NA)
```
* No they are not next to each other.
```r
row_sums = rowSums(edata)
edata = edata[order(row_sums),]
index = which(rank(-row_sums) < 500 )
heatmap(edata[index,],Rowv=NA,Colv=NA)
```

## Question 8
Load the Bodymap data using the following code:
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bodymap_eset.RData")
load(file=con)
close(con)
bm = bodymap.eset
pdata = pData(bm)
edata = exprs(bm)
```
Make an MA-plot of the first sample versus the second sample using the log2 transform (hint: you may have to add 1 first) and the 
```rlog``` transform from the DESeq2 package. How are the two MA-plots different? Which kind of genes appear most different in each plot?
* The plots look pretty similar, but the ```rlog``` transform seems to shrink the low abundance genes more. In both cases, the genes in the middle of the expression distribution show the biggest differences.
* The plots are very different, there are two strong diagonal stripes (corresponding to the zero count genes) in the ```log2``` plot and the high abundance genes are most different, but the low abundance genes seem to show smaller differences with the ```rlog``` transform
* The plots look pretty similar, but there are two strong diagonal stripes (corresponding to the zero count genes) in the ```rlog``` plot. In both cases, the genes in the middle of the expression distribution show the biggest differences, but the low abundance genes seem to show smaller differences with the ```log2``` transform.
* The plots look pretty similar, but the ```log2``` plot seems to do a better job of shrinking the low abundance genes toward each other. In both cases, the genes in the middle of the expression distribution show the biggest differences.






