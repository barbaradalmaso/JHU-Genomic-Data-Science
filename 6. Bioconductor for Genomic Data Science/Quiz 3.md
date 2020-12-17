## Quiz 3

## Question 1.
**Question:** What is the mean expression across all features for sample 5 in the ALL dataset (from the ALL package)?
* 6.146596
* 5.629627
* 4.875719
* 5.484443

## Question 2
We will use the biomaRt package to annotate an Affymetrix microarray. We want our results in the hg19 build of the human genome and we therefore need to connect to Ensembl 75 which is the latest release on this genome version. How to connect to older versions of Ensembl is described in the biomaRt package vignette; it can be achived with the command 
```mart <- useMart(host='feb2014.archive.ensembl.org', biomart = "ENSEMBL_MART_ENSEMBL")```

**Question:** Using this version of Ensembl, annotate each feature of the ALL dataset with the Ensembl gene id. How many probesets (features) are annotated with more than one Ensembl gene id?
* 1045
* 1270
* 951
* 1314

## Question 3
**Question:** How many probesets (Affymetrix IDs) are annotated with one or more genes on the autosomes (chromosomes 1 to 22).
* 9144
* 11016
* 9451
* 11488

## Question 4
Use the MsetEx dataset from the minfiData package. Part of this question is to use the help system to figure out how to address the question.

**Question:** What is the mean value of the Methylation channel across the features for sample “5723646052_R04C01”?
* 6672.703
* 7852.287
* 7932.841
* 7228.277

## Question 5
**Question:** Access the processed data from NCBI GEO Accession number GSE788. What is the mean expression level of sample GSM9024?
* 691.7748
* 779.3406
* 812.5740
* 756.432

## Question 6
We are using the airway dataset from the airway package.

**Question:** What is the average of the average length across the samples in the expriment?
* 84.25
* 144.75
* 114.00
* 113.75

## Question 7
We are using the airway dataset from the airway package. The features in this dataset are Ensembl genes.

**Question:** What is the number of Ensembl genes which have a count of 1 read or more in sample SRR1039512?
* 26068
* 23486
* 27534
* 25699

## Question 8
**Question:** The airway dataset contains more than 64k features. How many of these features overlaps with transcripts on the autosomes (chromosomes 1-22) as represented by the TxDb.Hsapiens.UCSC.hg19.knownGene package?

**Clarification:** A feature has to overlap the actual transcript, not the intron of a transcript. So you will need to make sure that the transcript representation does not contain introns.
* 27515
* 26276
* 28317
* 28264

## Question 9
The expression measures of the airway dataset are the number of reads mapping to each feature. In the previous question we have established that many of these features do not overlap autosomal transcripts from the TxDb.Hsapiens.UCSC.hg19.knownGene. But how many reads map to features which overlaps these transcripts?

**Question:** For sample SRR1039508, how big a percentage (expressed as a number between 0 and 1) of the total reads in the airway dataset for that sample, are part of a feature which overlaps an autosomal TxDb.Hsapiens.UCSC.hg19.knownGene transcript?
* 0.8749644
* 0.8546978
* 0.9004193
* 0.9752278

## Question 10
Consider sample SRR1039508 and only consider features which overlap autosomal transcripts from TxDb.Hsapiens.UCSC.hg19.knownGene. We should be able to very roughly divide these transcripts into expressed and non expressed transcript. Expressed transcripts should be marked by H3K4me3 at their promoter. The airway dataset have assayed “airway smooth muscle cells”. In the Roadmap Epigenomics data set, the E096 is supposed to be “lung”. Obtain the H3K4me3 narrowPeaks from the E096 sample using the AnnotationHub package.

**Question:** What is the median number of counts per feature (for sample SRR1039508) containing a H3K4me narrowPeak in their promoter (only features which overlap autosomal transcripts from TxDb.Hsapiens.UCSC.hg19.knownGene are considered)?

**Clarification:** We are using the standard 2.2kb default Bioconductor promotor setting.

Conclusion Compare this to the median number of counts for features without a H3K4me3 peak. Note that this short analysis has not taken transcript lengths into account and it compares different genomic regions to each other; this is highly suscepticle to bias such as sequence bias.
* 244
* 231
* 222
* 232
