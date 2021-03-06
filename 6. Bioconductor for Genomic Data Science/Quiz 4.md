# Quiz 4

## Question 1
The [yeastRNASeq](http://bioconductor.org/packages/release/bioc/html/yeastRNASeq.html)
experiment data package contains FASTQ files from an RNA seq experiment in yeast. When the package is installed, you can access one of the FASTQ files 
by the path given by 
```r
library(yeastRNASeq)
fastqFilePath <- system.file("reads", "wt_1_f.fastq.gz", package = "yeastRNASeq")
```
**Question:** What fraction of reads in this file has an A nucleotide in the 5th base of the read?
```r
library(ShortRead)
library(Biostrings)

# read fastq file
reads <- readFastq(fastqFilePath)
DNAStringSet <- sread(reads)

# fraction of reads has an A in the 5th base
cm <- consensusMatrix(DNAStringSet, as.prob=TRUE, baseOnly=TRUE)
cm['A', 5]

##   -------
##        A 
## 0.363841
```
* 0.3638
* 0.3170
* 0.2108
* 0.5828
### Answer
```
0.363841
```
## Question 2
This is a continuation of Question 1.

**Question:** What is the average numeric quality value of the 5th base of these reads?
```r
mean(as(quality(reads), "matrix")[,5])

##   -------
## [1] 28.93346
```
* 33.47
* 28.93
* 31.87
* 31.21
### Answer
```
28.93346
```

## Question 3
The [leeBamViews](http://bioconductor.org/packages/release/bioc/html/leeBamViews.html) experiment data package contains aligned BAM files from an RNA seq experiment in yeast (the same experiment as in Questions 1 and 2, but that is not pertinent to the question). You can access one of the BAM files by the path given by
```r
bamFilePath <- system.file("bam", "isowt5_13e.bam", package="leeBamViews")
```
These reads are short reads (36bp) and have been aligned to the genome using a standard aligner, ie. potential junctions have been ignored (this makes some sense as yeast has very few junctions and the reads are very short).

A read duplicated by position is a read where at least one more read shares the same position.

We will focus on the interval from 800,000 to 801,000 on yeast chromosome 13.

**Question:** In this interval, how many reads are duplicated by position?
```r
library(Rsamtools)

bamFile <- BamFile(bamFilePath)

# focus on Scchr13, interval from 800,000 to 801,000
gr <- GRanges(seqnames = "Scchr13", ranges = IRanges(start = c(800000), end = c(801000)))
params <- ScanBamParam(which = gr, what = scanBamWhat())
aln <- scanBam(bamFile, param = params)

# find duplicates
sum(table(aln[[1]]$pos)) - sum(table(aln[[1]]$pos) == 1)

##   -------
## [1] 129
```
* 129.00
* 299.00
* 330.00
* 10.00
### Answer
```
129
```

## Question 4
This is a continuation of Question 3.

The package contains 8 BAM files in total, representing 8 different samples from 4 groups. A full list of file paths can be had as
```r
bpaths <- list.files(system.file("bam", package="leeBamViews"), pattern = "bam$", full=TRUE)
```
An objective of the original paper was the discovery of novel transcribed regions in yeast. One such region is Scchr13:807762-808068.

**Question:** What is the average number of reads across the 8 samples falling in this interval?
```r
# focus on the novel transcribed regions
bamView <- BamViews(bpaths)
gr_nt <- GRanges(seqnames="Scchr13", ranges=IRanges(start = c(807762), end = c(808068)))
bamRanges(bamView) <- gr_nt
aln_nt <- scanBam(bamView)

# get sequences for each sample
alns <- lapply(aln_nt, function(xx) xx[[1]]$seq)

# calculate the average number of reads across 8 the samples
alns_len_sum = 0
for (i in 1:length(alns)){
  alns_len_sum = alns_len_sum + length(alns[i][[1]])
}
alns_len_sum / length(alns)

##   -------
## [1] 90.25
```
* 1792.00
* 1694.25
* 2030.75
* 90.25
### Answer
```
90.25
```

## Question 5
In the lecture on the oligo package an ExpressionSet with 18 samples is constructed, representing normalized data from an Affymetrix gene expression microarray. The samples are divided into two groups given by the 
```group``` variable.

**Question:** What is the average expression across samples in the control group for the “8149273” probeset (this is a character identifier, not a row number).
```r
library(oligo)
library(GEOquery)

# get data
getGEOSuppFiles("GSE38792")
untar("GSE38792/GSE38792_RAW.tar", exdir = "GSE38792/CEL")

# read data
celfiles <- list.files("GSE38792/CEL", full = TRUE)
rawData <- read.celfiles(celfiles)

# parse pData
filename <- sampleNames(rawData)
pData(rawData)$filename <- filename
sampleNames <- sub(".*_", "", filename)
sampleNames <- sub(".CEL.gz$", "", sampleNames)
sampleNames(rawData) <- sampleNames
pData(rawData)$group <- ifelse(grepl("^OSA", sampleNames(rawData)), "OSA", "Control")

# find "8149273" probeset
normData <- rma(rawData)
loc <- match("8149273", rownames(normData))

# average expression in control group
mean(exprs(normData[loc,])[1:8])


##   -------
## [1] 7.02183
```
* 9.560
* 7.0218
* 10.042
* 9.363
### Answer
```
7.02183
```

## Question 6
This is a continuation of Question 5.

Use the limma package to fit a two group comparison between the control group and the OSA group, and borrow strength across the genes using ```eBayes().``` Include all 18 samples in the model fit.

**Question:** What is the absolute value of the log foldchange
```(logFC)``` of the gene with the lowest ```P.value```.
```r
library(limma)

# use limma to fit between control group and OSA group
normData$group <- factor(normData$group)
design <- model.matrix(~normData$group)
fit <- lmFit(normData, design)
fit <- eBayes(fit)

# absolute value of logFC which has lowest P.value
abs(topTable(fit)$logFC[1])

##   -------
## [1] 0.7126484
```
* 0.7126
* 4.56
* 4.37
* 0.38
### Answer
```
0.7126484
```

## Question 7
This is a continuation of Question 6.

Question: How many genes are differentially expressed between the two groups at an 
```adj.P.value``` cutoff of 0.05?
```r
fit_toptable <- topTable(fit)
de <- subset(fit_toptable, adj.P.Val < 0.05)
de

##   -------
## ## [1] logFC     AveExpr   t         P.Value   adj.P.Val B        
## <0 rows> (or 0-length row.names)
```
* 0
* 232
* 760
* 22
### Answer
```
0
```

## Question 8
An example 450k dataset is contained in the [minfiData](http://bioconductor.org/packages/release/bioc/html/minfiData.html) package. This dataset contains 6 samples; 3 cancer and 3 normals. Cancer has been shown to be globally hypo-methylated (less methylated) compared to normal tissue of the same kind.

Take the RGsetEx dataset in this package and preprocess it with the preprocessFunnorm function. For each sample, compute the average Beta value (percent methylation) across so-called OpenSea loci.

**Question:** What is the mean difference in beta values between the 3 normal samples and the 3 cancer samples, across OpenSea CpGs?
```r
library(minfi)
library(minfiData)

# get OpenSea loci in RGsetEx with preprocess
rgSet <- preprocessFunnorm(RGsetEx)
rg_opensea <- rgSet[c(getIslandStatus(rgSet) == "OpenSea")]

# get Beta value in both group
rg_beta <- getBeta(rg_opensea)
normal <- mean(rg_beta[, c(1,2,5)])
cancer <- mean(rg_beta[, c(3,4,6)])

# mean difference between normal and cancer group
normal - cancer

##   -------
## [1] 0.08863657
```
* 0.0846
* 0.1914
* 0.0585
* 0.0054
### Answer
```
0.0846
```

## Question 9
Pergunta 9
This is a continuation of Question 8.

The Caco2 cell line is a colon cancer cell line profiled by ENCODE. Obtain the narrowPeak DNase hyper sensitive sites computed by the analysis working group (AWG).

**Question:** How many of these DNase hypersensitive sites contain one or more CpGs on the 450k array?
```r
library(AnnotationHub)

# get Caco2 data
ah <- AnnotationHub()
ah <- subset(ah, species=="Homo sapiens")
ah_Caco2 <- query(ah, c("Caco2", "AWG"))
ah_Caco2 <- ah_Caco2[["AH22442"]]

CpG_450K <- granges(rgSet)

unique(findOverlaps(CpG_450K, ah_Caco2, type="within"))

## Hits object with 68183 hits and 0 metadata columns:
##           queryHits subjectHits
##           <integer>   <integer>
##       [1]        40           9
##       [2]        51          10
##       [3]        52          10
##       [4]        53          10
##       [5]        71          11
##       ...       ...         ...
##   [68179]    485086      122978
##   [68180]    485087      122978
##   [68181]    485090      122979
##   [68182]    485091      122979
##   [68183]    485274      123007
##   -------
##   queryLength: 485512 / subjectLength: 123048
```
* 2714
* 95683
* 40151
* 29265
### Answer
```
40151
```

## Question 10
The [zebrafishRNASeq](http://bioconductor.org/packages/release/bioc/html/zebrafishRNASeq.html) package contains summarized data from an RNA-seq experiment in zebrafish in the form of a data.frame called 
```zfGenes``` The experiment compared 3 control samples to 3 treatment samples.

Each row is a transcript; the data.frame contains 92 rows with spikein transcripts; these have a rowname starting with “ERCC”. Exclude these rows from the analysis.

Use [DESeq2](http://bioconductor.org/packages/release/bioc/html/DESeq2.html)
to perform a differential expression analysis between control and treatment. Do not discard (filter) genes and use the ```padj``` results output as the p-value.

**Question:** How many features are differentially expressed between control and treatment (ie. 
```padj <= 0.05```?
```r
library(DESeq2)
library(zebrafishRNASeq)

# get and parse data
data("zfGenes")
zf <- zfGenes[grep("^ERCC", rownames(zfGenes), invert = T), ]
zf <- as.matrix(zf)
colData <- DataFrame(sampleID = colnames(zf), group = as.factor(c("control", "control", "control", "treatment", "treatment", "treatment")))

# perform DESeq2
dds <- DESeqDataSetFromMatrix(zf, colData, design = ~ group)
dds <- DESeq(dds)

# find differentially expressed features
res <- results(dds)
sigRes <- subset(res, padj <= 0.05)
dim(sigRes)[1]

##   -------
## [1] 116
```
* 87
* 426
* 401
* 30
### Answer
```
87
```
