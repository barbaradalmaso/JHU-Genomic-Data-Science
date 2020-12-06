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
```
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

**Question:** How many islands exists on the autosomes?
* 26641
* 24696
* 26567
* 25495
```
Answer:
```

## Question 2
**Question:** How many CpG Islands exists on chromosome 4?
Given the following code in Python:
* 1011
* 1004
* 1031
* 1019
```
Answer:
```

## Question 3
Obtain the data for the H3K4me3 histone modification for the H1 cell line from Epigenomics Roadmap, using AnnotationHub. Subset these regions to only keep regions mapped to the autosomes (chromosomes 1 to 22).

**Question:** How many bases does these regions cover?
* 41135164
* 43087951
* 41553593
* 42682454
```
Answer:
```

## Question 4
Obtain the data for the H3K27me3 histone modification for the H1 cell line from Epigenomics Roadmap, using the AnnotationHub package. Subset these regions to only keep regions mapped to the autosomes. In the return data, each region has an associated "signalValue".

**Question:** What is the mean signalValue across all regions on the standard chromosomes?
* 4.770728
* 4.917626
* 4.517959
* 4.419120
```
Answer:
```

## Question 5
Bivalent regions are bound by both H3K4me3 and H3K27me3.

**Question:** Using the regions we have obtained above, how many bases on the standard chromosomes are bivalently marked?
* 9926503
* 10289096
* 10984729
* 10207246
```
Answer:
```

## Question 6
We will examine the extent to which bivalent regions overlap CpG Islands.

**Question:** how big a fraction (expressed as a number between 0 and 1) of the bivalent regions, overlap one or more CpG Islands?
* 0.5893028
* 0.5383644
* 0.496077
* 0.5621946
```
Answer:
```

## Question 7
**Question:** How big a fraction (expressed as a number between 0 and 1) of the bases which are part of CpG Islands, are also bivalent marked?
* 0.1860021
* 0.2924248
* 0.241688
* 0.2750512
```
Answer:
```

## Question 8
**Question:** How many bases are bivalently marked within 10kb of CpG Islands?
**Tip**: consider using the "resize()"" function
* 11928130
* 7920203
* 11104114
* 9782086
```
Answer:
```

## Question 9
**Question:** How big a fraction (expressed as a number between 0 and 1) of the human genome is contained in a CpG Island?

**Tip 1:** the object returned by AnnotationHub contains "seqlengths".
**Tip 2:** you may encounter an integer overflow. As described in the session on R Basic Types, you can address this by converting integers to numeric before summing them, "as.numeric()".
* 0.007047481
* 0.005769540
* 0.006823921
* 0.007288502
```
Answer: int, float, float, float, int, str, str, int, float
```

## Question 10
**Question:** Compute an odds-ratio for the overlap of bivalent marks with CpG islands.

* 169.0962
* 138.4391
* 156.0433
* 160.4022
```
Answer:
```
