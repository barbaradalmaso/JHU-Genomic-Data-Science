# Quiz 1

```R
## load ipak function to check if selected packages are installed, 
##  installs them if they are not,
##  then load them into the R session. 
  
ipak <- function(pkg){
    new.pkg <- pkg[!(pkg %in% installed.packages()[, "Package"])]
    if (length(new.pkg)) 
        install.packages(new.pkg, dependencies = TRUE)
    sapply(pkg, require, character.only = TRUE)
}

## usage
packages = c('AnnotationHub', 'GenomicRanges', 'rtracklayer')
ipak(packages)

## AnnotationHub GenomicRanges   rtracklayer 
##          TRUE          TRUE          TRUE
```

## Question 1
Use the AnnotationHub package to obtain data on "CpG Islands" in the human genome.
**Question:** How many islands exists on the autosomes?
```R
ah <- AnnotationHub()

ah_human_CpG <- query(ah, c("CpG Islands", "hg19"))
# ah_human_CpG # Used to check output
ah_human_CpG_data <- ah_human_CpG[["AH5086"]]
# ah_human_CpG_data # Used to check output

#######################################
# summary info about CpG island dataset
# Used to check output
# summary(width(ah_human_CpG_data))
# seqinfo(ah_human_CpG_data)
# seqlevels(ah_human_CpG_data)
# gaps(ah_human_CpG_data)
#######################################

# reduce data
ah_human_CpG_reduce <- reduce(ah_human_CpG_data)
# ah_human_CpG_reduce # Used to check output

# count number of CpG islands in autochromosome
autosome <- c(paste("chr", 1:22, sep=""))
split_data_by_chr <- split(ah_human_CpG_reduce, seqnames(ah_human_CpG_reduce))
autosome_CpG_data <- split_data_by_chr[autosome]
# seqlevels(autosome_CpG_data) # Used to check output

# CpG Islands on autosome
unlist(autosome_CpG_data)
```
```R
## GRanges object with 26641 ranges and 0 metadata columns:
##         seqnames               ranges strand
##            <Rle>            <IRanges>  <Rle>
##    chr1     chr1     [ 28736,  29810]      *
##    chr1     chr1     [135125, 135563]      *
##    chr1     chr1     [327791, 328229]      *
##    chr1     chr1     [437152, 438164]      *
##    chr1     chr1     [449274, 450544]      *
##     ...      ...                  ...    ...
##   chr22    chr22 [51135671, 51136118]      *
##   chr22    chr22 [51142803, 51143308]      *
##   chr22    chr22 [51158387, 51160060]      *
##   chr22    chr22 [51169028, 51170019]      *
##   chr22    chr22 [51221773, 51222317]      *
##   -------
##   seqinfo: 93 sequences (1 circular) from hg19 genome
```
* 26641
* 24696
* 26567
* 25495
```
Answer:26641
```

## Question 2
**Question:** How many CpG Islands exists on chromosome 4?
```R
# CpG Islands on chr4
autosome_CpG_data[4]
```
```R
## GRangesList object of length 1:
## $chr4 
## GRanges object with 1031 ranges and 0 metadata columns:
##          seqnames                 ranges strand
##             <Rle>              <IRanges>  <Rle>
##      [1]     chr4       [ 53199,  53672]      *
##      [2]     chr4       [107147, 107898]      *
##      [3]     chr4       [124333, 124841]      *
##      [4]     chr4       [206378, 206892]      *
##      [5]     chr4       [298804, 299312]      *
##      ...      ...                    ...    ...
##   [1027]     chr4 [190939802, 190940591]      *
##   [1028]     chr4 [190942735, 190944898]      *
##   [1029]     chr4 [190959045, 190960011]      *
##   [1030]     chr4 [190962112, 190962689]      *
##   [1031]     chr4 [190986383, 191013609]      *
## 
## -------
## seqinfo: 93 sequences (1 circular) from hg19 genome
```
* 1011
* 1004
* 1031
* 1019
```
Answer: 1031
```

## Question 3
Obtain the data for the H3K4me3 histone modification for the H1 cell line from Epigenomics Roadmap, using AnnotationHub. Subset these regions to only keep regions mapped to the autosomes (chromosomes 1 to 22).

**Question:** How many bases does these regions cover?
```R
ah_H3K4me <- query(ah, c("H3K4me3", "E003"))
ah_H3K4me_data <- ah_H3K4me[["AH29884"]]
# seqinfo(ah_H3K4me_data)
# seqlevels(ah_H3K4me_data)

# subset autosome data
ah_H3K4me_autosome_data <- subset(ah_H3K4me_data, seqnames %in% autosome)
# count base pairs
sum(width(unlist(ah_H3K4me_autosome_data)))

##   -------
## [1] 41135164
```
* 41135164
* 43087951
* 41553593
* 42682454
```
Answer: 41135164
```

## Question 4
Obtain the data for the H3K27me3 histone modification for the H1 cell line from Epigenomics Roadmap, using the AnnotationHub package. Subset these regions to only keep regions mapped to the autosomes. In the return data, each region has an associated "signalValue".

**Question:** What is the mean signalValue across all regions on the standard chromosomes?
```R
ah_H3K27me3 <- query(ah, c("H3K27me3", "narrowPeak", "E003"))
# ah_H3K27me3

# retrieve data
ah_H3K27me3_data <- ah_H3K27me3[["AH29892"]]

# summary(width(ah_H3K27me3_data))
# seqlevels(ah_H3K27me3_data)
# seqinfo(ah_H3K27me3_data)
# subset standard chrosome data

ah_H3K27me3_autosome_data <- subset(ah_H3K27me3_data, seqnames %in% autosome)

# calculate mean signalValue
ah_H3K27me3_autosome_data_mean <- mean(ah_H3K27me3_autosome_data$signalValue)
ah_H3K27me3_autosome_data_mean

##   -------
## [1] 4.770728
```
* 4.770728
* 4.917626
* 4.517959
* 4.419120
```
Answer: 4.770728
```

## Question 5
Bivalent regions are bound by both H3K4me3 and H3K27me3.

**Question:** Using the regions we have obtained above, how many bases on the standard chromosomes are bivalently marked?
```R
bivalent_data <- intersect(unlist(ah_H3K4me_autosome_data), unlist(ah_H3K27me3_autosome_data))
sum(width(reduce(bivalent_data)))

##   -------
## [1] 10289096
```

* 9926503
* 10289096
* 10984729
* 10207246
```
Answer: 10289096
```

## Question 6
We will examine the extent to which bivalent regions overlap CpG Islands.

**Question:** how big a fraction (expressed as a number between 0 and 1) of the bivalent regions, overlap one or more CpG Islands?
```R
CpG_bivalent_data <- findOverlaps(bivalent_data, unlist(autosome_CpG_data))
fraction_bi <- length(unique(queryHits(CpG_bivalent_data)))/length(bivalent_data)
fraction_bi

##   -------
## [1] 0.5383644
```
* 0.5893028
* 0.5383644
* 0.496077
* 0.5621946
```
Answer: 0.5383644
```

## Question 7
**Question:** How big a fraction (expressed as a number between 0 and 1) of the bases which are part of CpG Islands, are also bivalent marked?
```R
ov_CpG_bivalent <- intersect(bivalent_data, unlist(autosome_CpG_data))
fraction_CpG <- sum(width(reduce(ov_CpG_bivalent)))/sum(width(unlist(autosome_CpG_data)))
fraction_CpG

##   -------
## [1] 0.241688
```
* 0.1860021
* 0.2924248
* 0.241688
* 0.2750512
```
Answer: 0.241688
```

## Question 8
**Question:** How many bases are bivalently marked within 10kb of CpG Islands?
**Tip**: consider using the "resize()"" function
```R
autosome_CpG_data
```
```R
## GRangesList object of length 22:
## $chr1 
## GRanges object with 2462 ranges and 0 metadata columns:
##          seqnames                 ranges strand
##             <Rle>              <IRanges>  <Rle>
##      [1]     chr1       [ 28736,  29810]      *
##      [2]     chr1       [135125, 135563]      *
##      [3]     chr1       [327791, 328229]      *
##      [4]     chr1       [437152, 438164]      *
##      [5]     chr1       [449274, 450544]      *
##      ...      ...                    ...    ...
##   [2458]     chr1 [249132081, 249133310]      *
##   [2459]     chr1 [249141564, 249142796]      *
##   [2460]     chr1 [249152412, 249153419]      *
##   [2461]     chr1 [249167409, 249168010]      *
##   [2462]     chr1 [249200253, 249200721]      *
## 
## ...
## <21 more elements>
## -------
## seqinfo: 93 sequences (1 circular) from hg19 genome
```
```R
CpG_10k <- resize(unlist(autosome_CpG_data), 
                  width = 20000 + width(unlist(autosome_CpG_data)), 
                  fix = "center")
CpG_10k_bivalent <- intersect(CpG_10k, bivalent_data)
sum(width(CpG_10k_bivalent))

##   -------
## [1] 9782086
```
* 11928130
* 7920203
* 11104114
* 9782086
```
Answer: 9782086
```

## Question 9
**Question:** How big a fraction (expressed as a number between 0 and 1) of the human genome is contained in a CpG Island?

**Tip 1:** the object returned by AnnotationHub contains "seqlengths".
**Tip 2:** you may encounter an integer overflow. As described in the session on R Basic Types, you can address this by converting integers to numeric before summing them, "as.numeric()".
```R
# calculate genome size
genome <- ah[["AH5018"]]
genome <- keepSeqlevels(genome, c("chr1", "chr2", "chr3", "chr4", "chr5", "chr6", "chr7", "chr8", "chr9", "chr10", "chr11", "chr12", "chr13", "chr14", "chr15", "chr16", "chr17", "chr18", "chr19", "chr20", "chr21", "chr22"))
genome_size <- sum(as.numeric(seqlengths(genome)))
# How big a fraction (expressed as a number between 0 and 1) of the human genome is contained in a CpG Island?
sum(as.numeric(width(unlist(autosome_CpG_data))))/genome_size

##   -------
## [1] 0.007047481
```
* 0.007047481
* 0.005769540
* 0.006823921
* 0.007288502
```
Answer: int, float, float, float, int, str, str, int, float
```

## Question 10
**Question:** Compute an odds-ratio for the overlap of bivalent marks with CpG islands.

```R
# odds ratio
inOut = matrix(0, ncol = 2, nrow = 2)
colnames(inOut) = c("in", "out")
rownames(inOut) = c("in", "out")
# inOut
inOut[1,1] = sum(width(intersect(bivalent_data, 
                                 unlist(autosome_CpG_data),
                                 ignore.strand=TRUE)))
inOut[1,2] = sum(width(setdiff(bivalent_data, 
                               unlist(autosome_CpG_data),
                               ignore.strand=TRUE)))
inOut[2,1] = sum(width(setdiff(unlist(autosome_CpG_data), 
                               bivalent_data, 
                               ignore.strand=TRUE)))
inOut[2,2] = genome_size - sum(inOut)

inOut
```
```R
##           in        out
## in   4907239    5381857
## out 15396787 2855347403
```

```R
odd_ratio <- inOut[1,1]*inOut[2,2]/(inOut[1,2]*inOut[2,1])
odd_ratio

##   -------
## [1] 169.0962
```
* 169.0962
* 138.4391
* 156.0433
* 160.4022
```
Answer: 169.0962
```
