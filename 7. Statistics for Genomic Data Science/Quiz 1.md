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
### Answer
```
All the data and code are available but the codebook does not fully explain the experimental design and all protocols for patient recruitment.
```

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
* The table is random each time you knit the document, but the plot is always the same after you knit it the first time.
* The plot is random the first time you knit the document. It is identical to the first time the second time you knit the document. After removing test_cache and test_files they generate new random versions.
* The plot and table are random the first time you knit the document. They are identical the second time you knit the document. After removing the folders test_cache and test_files they are still identical.
* The plot and table are random every time you kint the document, except for the last time.
### Answer
```
The plot is random the first time you knit the document. It is identical to the first time the second time you knit the document. After removing the folders test_cache and test_files they generate new random versions.
```

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
### Answer
```
Get the genomic table with assay(se), get the phenotype table with colData(se), get the feature data with rowRanges(se). rowRanges(se) gives information on the genomic location and structure of the measured
```

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
### Answer
```
(a) By looking at variation across samples from 10 different healthy individuals 
(b) By looking at variability between the measurements on the two sub-samples from the same sample and 
(c) by comparing the average measurements on the healthy individuals to the measurements on the individuals with cancer. 
```

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
* The covariates in the Bottomly data set (experiment number, lane number)  are balanced with respect to strain. The covariates in the Bodymap data set (gender, age, number of technical replicates) are not balanced with respect to tissue.   
* The Bottomly data has a smaller sample size than the Bodymap data.
* The Bodymap data has measured more levels of the outcome of interest (tissues) than the Bottomly data has measured (strains).
* The Bodymap data has more technical replicates than the Bottomly data.
### Answer
```
The covariates in the Bottomly data set (experiment number, lane number) are balanced with respect to strain. The covariates in the Bodymap data set (gender, age, number of technical replicates) are not balanced with respect to tissue.
```

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
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%201/unnamed-chunk-5-1.png)
* The plot uses rainbow colors which are hard for color blind individuals to see. 
* Humans are much worse at comparing angles than comparing position or length.
* The plot would be much easier to see if the pie chart were rotated by 90 degrees from its current position. 
* The data could much more easily be shown as a heatmap. 
### Answer
```
The data could much more easily be shown as a heatmap. 
```

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
edata = edata[order(-row_sums),]
index = 1:500
heatmap(edata[index,],Rowv=NA,Colv=NA)
```
* The highly expressed samples are next to each other.
```r
row_sums = rowSums(edata)
index = which(rank(row_sums) < 500 )
heatmap(edata[index,],Colv=NA)
```
* The highly expressed samples are not next to each other.
```r
row_sums = rowSums(edata)
edata = edata[order(row_sums),]
index = which(rank(-row_sums) < 500 )
heatmap(edata[index,],Rowv=NA,Colv=NA)
```
* No they are not next to each other.
```r
row_sums = rowSums(edata)
index = which(rank(-row_sums) < 500 )
heatmap(edata[index,],Rowv=NA,Colv=NA)
```
### Answer
```
row_sums = rowSums(edata)
edata = edata[order(-row_sums),]
index = 1:500
heatmap(edata[index,],Rowv=NA,Colv=NA)
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%201/heatmap1.png)

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
### Answer
```
The plots look pretty similar, but the rlog transform seems to shrink the low abundance genes more. In both cases, the genes in the middle of the expression distribution show the biggest differences.
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%201/Graph1.png)
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%201/Graph2.png)

## Question 9
Load the Montgomery and Pickrell eSet:
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/montpick_eset.RData")
load(file=con)
close(con)
mp = montpick.eset
pdata=pData(mp)
edata=as.data.frame(exprs(mp))
fdata = fData(mp)
```
Cluster the data in three ways:

1. With no changes to the data
2. After filtering all genes with ```rowMeansrowMeans``` less than 100
3. After taking the ```log2``` transform of the data without filtering

Color the samples by which study they came from (Hint: consider using the function ```myplclust.R``` in the package ```rafalib``` available from CRAN and looking at the argument ```lab.col.```

How do the methods compare in terms of how well they cluster the data by study? Why do you think that is?
* Clustering with or without filtering is about the same. Clustering after the log2 transform shows better clustering with respect to the study variable. The likely reason is that the highly skewed distribution doesn't match the Euclidean distance metric being used in the clustering example.
* Clustering is identical with all three approaches and they show equal clustering. The distance is an average over all the dimensions so it doesn't change. 
* Clustering with or without log2 transform is about the same. Clustering after filtering shows better clustering with respect to the study variable. The reason is that the lowly expressed genes have some extreme outliers that skew the calculation. 
* Clustering is identical with all three approaches and they show equal clustering. The log2 transform is a monotone transformation so it doesn't affect the clustering.
### Answer
```
Clustering with or without filtering is about the same. Clustering after the log2 transform shows better clustering with respect to the study variable. The likely reason is that the highly skewed distribution doesn't match the Euclidean distance metric being used in the clustering example.
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%201/origin.png)
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%201/remove%20low%20expression.png)
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%201/log2%20transform.png)

## Question 10
Load the Montgomery and Pickrell eSet:
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/montpick_eset.RData")
load(file=con)
close(con)
mp = montpick.eset
pdata=pData(mp)
edata=as.data.frame(exprs(mp))
fdata = fData(mp)
```
Cluster the samples using k-means clustering after applying the 
```log2``` transform (be sure to add 1). Set a seed for reproducible results (use ```set.seed(1235)```). If you choose two clusters, do you get the same two clusters as you get if you use the ```cutree``` function to cluster the samples into two groups? Which cluster matches most closely to the study labels?
* They produce different clusterings with hierarchical clustering more closely matching the study variable. K-means clustering is too random to pick up the study difference. 
* They produce different answers, with hierarchical clustering giving a much more unbalanced clustering. The k-means clustering matches study better. 
* They produce different answers, with k-means clustering giving a much more unbalanced clustering. The hierarchical clustering matches study better. 
* They produce the same answers and match the study variable equally well. 
### Answer
```
They produce different answers, with hierarchical clustering giving a much more unbalanced clustering. The k-means clustering matches study better.
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%201/matplot.png)
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%201/cutree.png)
