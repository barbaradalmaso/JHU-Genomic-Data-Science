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
UCSC mm9
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
```r
# perform a differential expression analysis using limma
mod = model.matrix(~ pdata_bot$strain)
fit_limma = lmFit(edata, mod)
ebayes_limma = eBayes(fit_limma)
limma_pvals = topTable(ebayes_limma,number=dim(edata)[1], adjust.method ="BH", p.value=0.05, sort.by='none')

# first DE gene
limma_pvals[1,]

##                        logFC  AveExpr         t      P.Value   adj.P.Val
## ENSMUSG00000000402 -1.222062 4.292471 -4.509076 5.312399e-05 0.004394846
##                           B
## ENSMUSG00000000402 1.583059
```
```r
# number of genes are differentially expressed at the 5% FPR level 
dim(limma_pvals)

## ------------
## [1] 223   6

```
* 223 at FDR 5%; ENSMUSG00000000402 first DE gene
* 223 at FDR 5%; ENSMUSG00000000001 first DE gene
* 9431 at FDR 5%; ENSMUSG00000027855 first DE gene
* 90 at FDR 5%; ENSMUSG00000000402 first DE gene
### Answer
```
223 at FDR 5%; ENSMUSG00000000402 first DE gene
```

## Question 3
Use the ```nullp``` and ```goseq``` functions in the ```goseq```
package to perform a gene ontology analysis. What is the top category that comes up as over represented? (hint: you will need to use the genome information on the genome from question 1 and the differential expression analysis from question 2.
```r
library(devtools)
library(Biobase)
library(goseq)
library(DESeq2)

# limma fit with p-value less than 0.05
limma_table = topTable(ebayes_limma,number=dim(edata)[1], adjust.method ="BH", sort.by='none')
genes = as.integer(limma_table$adj.P.Val < 0.05)
names(genes) = rownames(edata)
not_na = !is.na(genes)
genes = genes[not_na]

# use nullp and goseq to perform a gene ontology analysis
pwf = nullp(genes, "mm9", "ensGene")
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%204/Graph1.png)
```r
GO.wall = goseq(pwf, "mm9", "ensGene")
GO.top10 = GO.wall[1:10,1]

# top category
GO.top10[1]

## ----------------
## [1] "GO:0004888"

```
* GO:0004888 
* GO:0008528
* GO:0038023
* GO:0001653
### Answer
```
GO:0004888
```

## Question 4
Look up the GO category that was the top category from the previous question. What is the name of the category? 
```r
GO.wall$term[1]

## ------------
## [1] "transmembrane signaling receptor activity"
```
* peptide receptor activity
* signaling receptor activity
* transmembrane signaling receptor activity
* G-protein coupled peptide receptor activity

### Answer
```
transmembrane signaling receptor activity
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
```r
# perform a differential expression analysis using limma, adjusting for lane as a factor
mod_adj = model.matrix(~ pdata_bot$strain + as.factor(pdata_bot$lane.number))
fit_limma_adj = lmFit(edata,mod_adj)
ebayes_limma_adj = eBayes(fit_limma_adj)

# find genes significant at 5% FPR rate
limma_table = topTable(ebayes_limma_adj, number=dim(edata)[1], adjust.method ="BH", sort.by='none')
genes = as.integer(limma_table$adj.P.Val < 0.05)
names(genes) = rownames(edata)
not_na = !is.na(genes)
genes = genes[not_na]

pwf = nullp(genes, "mm9", "ensGene")
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%204/Graph2.png)
```r
GO.wall = goseq(pwf, "mm9", "ensGene")
GO.top10_adj = GO.wall[1:10,1]

# top 10 overrepresented categories are the same
intersect(GO.top10, GO.top10_adj)

## --------------
## [1] "GO:0007129" "GO:0070192" "GO:0045143" "GO:0007127"
```
* 0
* 2
* 3
* 5
### Answer
```
2
```
