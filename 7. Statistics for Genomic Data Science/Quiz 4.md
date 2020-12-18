# Module 4 Quiz

## Question 1
1. When performing gene set analysis it is critical to use the same annotation as was used in pre-processing steps. 
Read the paper behind the Bottomly data set on the ReCount database: http://www.ncbi.nlm.nih.gov/pubmed?term=21455293

Using the paper and the function: ```supportedGenomes()``` in the ```goseq package``` can you figure out which of the Mouse genome builds they aligned the reads to.
* UCSC mm9
* UCSC hg18
* Genome Reference Consortium GRCm38
* NCBI Build 35
### Answer
```

```

## Question 2
Load the Bottomly data with the following code and perform a differential expression analysis using 
```limma``` with only the strain variable as an outcome. How many genes are differentially expressed at the 5% FDR level using Benjamini-Hochberg correction? What is the gene identifier of the first gene differentially expressed at this level (just in order, not the smallest FDR) ? (hint: the 
```featureNames``` function may be useful)
```r
library(Biobase)
library(limma)
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bottomly_eset.RData")
load(file=con)
close(con)
bot = bottomly.eset
pdata_bot=pData(bot)
fdata_bot = featureData(bot)
edata = exprs(bot)
fdata_bot = fdata_bot[rowMeans(edata) > 5]
edata = edata[rowMeans(edata) > 5, ]
edata = log2(edata+1)
```
* 223 at FDR 5%; ENSMUSG00000000402 first DE gene
* 223 at FDR 5%; ENSMUSG00000000001 first DE gene
* 9431 at FDR 5%; ENSMUSG00000027855 first DE gene
* 90 at FDR 5%; ENSMUSG00000000402 first DE gene
### Answer
```

```

## Question 3
Use the ```nullp``` and ```goseq``` functions in the ```goseq```
package to perform a gene ontology analysis. What is the top category that comes up as over represented? (hint: you will need to use the genome information on the genome from question 1 and the differential expression analysis from question 2.
* GO:0004888 
* GO:0008528
* GO:0038023
* GO:0001653
### Answer
```

```

## Question 4
Look up the GO category that was the top category from the previous question. What is the name of the category? 
* peptide receptor activity
* signaling receptor activity
* transmembrane signaling receptor activity
* G-protein coupled peptide receptor activity
### Answer
```

```

## Question 5
Load the Bottomly data with the following code and perform a differential expression analysis using 
```limma``` and treating strain as the outcome but adjusting for lane as a factor. Then find genes significant at the 5% FDR rate using the Benjamini Hochberg correction and perform the gene set analysis with 
```goseq``` following the protocol from the first 4 questions. How many of the top 10 overrepresented categories are the same for the adjusted and unadjusted analysis?
```r
library(Biobase)
library(limma)
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bottomly_eset.RData")
load(file=con)
close(con)
bot = bottomly.eset
pdata_bot=pData(bot)
fdata_bot = featureData(bot)
edata = exprs(bot)
fdata_bot = fdata_bot[rowMeans(edata) > 5]
edata = edata[rowMeans(edata) > 5, ]
```
* 0
* 2
* 3
* 5
### Answer
```

```
