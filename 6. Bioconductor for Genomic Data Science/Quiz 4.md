# Quiz 4

The (yeastRNASeq)[http://bioconductor.org/packages/release/bioc/html/yeastRNASeq.html]
experiment data package contains FASTQ files from an RNA seq experiment in yeast. When the package is installed, you can access one of the FASTQ files 
by the path given by 
```r
library(yeastRNASeq)
fastqFilePath <- system.file("reads", "wt_1_f.fastq.gz", package = "yeastRNASeq")
```
**Question:** What fraction of reads in this file has an A nucleotide in the 5th base of the read?
* 0.3638
* 0.3170
* 0.2108
* 0.5828

## Question 2
This is a continuation of Question 1.

**Question:** What is the average numeric quality value of the 5th base of these reads?
* 33.47
* 28.93
* 31.87
* 31.21

## Question 3
The (leeBamViews)[http://bioconductor.org/packages/release/bioc/html/leeBamViews.html] experiment data package contains aligned BAM files from an RNA seq experiment in yeast (the same experiment as in Questions 1 and 2, but that is not pertinent to the question). You can access one of the BAM files by the path given by
```r
bamFilePath <- system.file("bam", "isowt5_13e.bam", package="leeBamViews")
```
These reads are short reads (36bp) and have been aligned to the genome using a standard aligner, ie. potential junctions have been ignored (this makes some sense as yeast has very few junctions and the reads are very short).

A read duplicated by position is a read where at least one more read shares the same position.

We will focus on the interval from 800,000 to 801,000 on yeast chromosome 13.

**Question:** In this interval, how many reads are duplicated by position?
* 129.00
* 299.00
* 330.00
* 10.00

## Question 4
This is a continuation of Question 3.

The package contains 8 BAM files in total, representing 8 different samples from 4 groups. A full list of file paths can be had as
```r
bpaths <- list.files(system.file("bam", package="leeBamViews"), pattern = "bam$", full=TRUE)
```
An objective of the original paper was the discovery of novel transcribed regions in yeast. One such region is Scchr13:807762-808068.

**Question:** What is the average number of reads across the 8 samples falling in this interval?
* 1792.00
* 1694.25
* 2030.75
* 90.25

## Question 5
In the lecture on the oligo package an ExpressionSet with 18 samples is constructed, representing normalized data from an Affymetrix gene expression microarray. The samples are divided into two groups given by the 
```group``` variable.

**Question:** What is the average expression across samples in the control group for the “8149273” probeset (this is a character identifier, not a row number).
* 9.560
* 7.0218
* 10.042
* 9.363

## Question 6
This is a continuation of Question 5.

Use the limma package to fit a two group comparison between the control group and the OSA group, and borrow strength across the genes using ```eBayes().``` Include all 18 samples in the model fit.

**Question:** What is the absolute value of the log foldchange
```(logFC)``` of the gene with the lowest ```P.value.```
* 0.7126
* 4.56
* 4.37
* 0.38

## Question 7
This is a continuation of Question 6.

Question: How many genes are differentially expressed between the two groups at an 
```adj.P.value``` cutoff of 0.05?
* 0
* 232
* 760
* 22

## Question 8
An example 450k dataset is contained in the (minfiData)[http://bioconductor.org/packages/release/bioc/html/minfiData.html] package. This dataset contains 6 samples; 3 cancer and 3 normals. Cancer has been shown to be globally hypo-methylated (less methylated) compared to normal tissue of the same kind.

Take the RGsetEx dataset in this package and preprocess it with the preprocessFunnorm function. For each sample, compute the average Beta value (percent methylation) across so-called OpenSea loci.

**Question:** What is the mean difference in beta values between the 3 normal samples and the 3 cancer samples, across OpenSea CpGs?
* 0.0846
* 0.1914
* 0.0585
* 0.0054

## Question 9
Pergunta 9
This is a continuation of Question 8.

The Caco2 cell line is a colon cancer cell line profiled by ENCODE. Obtain the narrowPeak DNase hyper sensitive sites computed by the analysis working group (AWG).

**Question:** How many of these DNase hypersensitive sites contain one or more CpGs on the 450k array?
* 2714
* 95683
* 40151
* 29265

## Question 10
The (zebrafishRNASeq)[http://bioconductor.org/packages/release/bioc/html/zebrafishRNASeq.html] package contains summarized data from an RNA-seq experiment in zebrafish in the form of a data.frame called 
```zfGenes``` The experiment compared 3 control samples to 3 treatment samples.

Each row is a transcript; the data.frame contains 92 rows with spikein transcripts; these have a rowname starting with “ERCC”. Exclude these rows from the analysis.

Use (DESeq2)[http://bioconductor.org/packages/release/bioc/html/DESeq2.html]
to perform a differential expression analysis between control and treatment. Do not discard (filter) genes and use the ```padj``` results output as the p-value.

***Question:*** How many features are differentially expressed between control and treatment (ie. 
```padj <= 0.05```?
* 87
* 426
* 401
* 30
