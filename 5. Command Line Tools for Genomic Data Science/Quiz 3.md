# Module 3 Quiz

## Question 1
Which of the following statements is FALSE:
* SNP refers to a Single Non-defined Polymorhism
* Differences in the genomes of individuals are strong contributors to their phenotypic variations.
* Different versions of a gene resulted from genomic mutations are called alleles.
* SNV refers to a Single Nucleotide Variant.
```
Answer: SNP refers to a Single Non-defined Polymorhism
```

## Question 2
Which of the following statements is FALSE:
* The VCF format shows the changes in amino acid resulting from the nucleotide mutation, in column 3.
* The mpileup format produced by SAMtools can be used to represent sites of variation.
* The software SAMtools can be used to analyze alignments of exome sequencing reads and to determine sites of variation.
* The VCF FORMAT lines specify the format used for the genotype data.Option text
```
Answer: The VCF format shows the changes in amino acid resulting from the nucleotide mutation, in column 3.
```

## Question 3
What program can be used to generate a list of candidate sites of variation in an exome data set:
* samtools tview
* head
* bwamem
* samtools mpileup
```
Answer: samtools mpileup
```

## Question 4
In a comprehensive effort to study genome variation in a patient cohort, you sequence and call variants in the exome, whole genome shotgun and RNA-seq data from each patient. Which of the following is FALSE when comparing these three types of resources:
* Exome sequencing comprehensively captures variants in the 3’ and 5’ UTRs of genes.
* Exome sequencing can capture variants in a pre-defined set of coding exons and their immediate surrounding area.
* Exome sequencing cannot determine variants in novel polymorphic alternative splicing events.
* Exome sequencing captures fewer variants than whole genome sequencing. Whole genome sequencing can potentially detect all variants that can be found with either exome sequencing or RNA-seq.
```
Answer: Exome sequencing comprehensively captures variants in the 3’ and 5’ UTRs of genes.
```

## Question 5
Which of the following options can be used to allow bowtie2 to generate partial alignments?
* --local
* -S
* –k
* -U
```
Answer: --local
```

## Question 6
Select the correct interpretation for the snippet of ‘mpileup’ output below.
```
Chr3  11700316  C 8 .$....... 8C@C;CB3
Chr3  11951491  G 16  AAAA,......aA..A  C2@2BCBCCCAC2CC4 
``` 
* Both sites show potential variation; the alternate letter for site 1 is $, and for site 2 is A; site 1 has 8 supporting reads, and site 2 has 16
* Both sites show potential variation; the alternate letter for site 1 is C, and for site 2 is G; site 1 has 8 supporting reads, and site 2 has 7
* Only site 2 shows potential variation; the alternate letter for site 2 is A; site 1 has 8 supporting reads, and site 2 has 16
* Both sites show potential variation the alternate letter for site 1 is $, and for site 2 is G; site 1 has 8 supporting reads, and site 2 has 16
```
Answer: Only site 2 shows potential variation; the alternate letter for site 2 is A; site 1 has 8 supporting reads, and site 2 has 16
```

## Question 7
Given the set of variants described in the VCF excerpt below, which of the following is FALSE?
```
##INFO=<ID=DP,Number=1,Type=Integer,Description="Raw read depth"
    >
##INFO=<ID=MQ,Number=1,Type=Integer,Description="Average mapping 
    quality">
##FORMAT=<ID=GT,Number=1,Type=String,Description="Genotype">
##FORMAT=<ID=PL,Number=G,Type=Integer,Description="List of Phred
    -scaled genotype likelihoods">
Chr3  11966312   .  G A 15.9  . DP=5;MQ=15    GT:PL   
    1/1:43,9,0
Chr3  11972108  . TAAAA TAAA  32.8  .  INDEL;IDV=7
    ;IMF=0.636364;DP=11;MQ=22 GT:PL 0/1:66,0,2
Chr3  13792328  rs145271872 G T 5.5 . DP=1;MQ=40  GT
    :PL 0/1:32,3,0
```
* The quality values for the three calls are 15.9, 32.8 and 5.5
* The sample contains only the alternate allele for variant 3
* The alternate allele for variant 3 is T
* The alternate allele for variant 1 is A
```
Answer: The sample contains only the alternate allele for variant 3
```

## Question 8
What does the following code do:
```
bowtie2 –x species/species –U in.fastq | grep –v “^@” | cut –f3 | 
    sort | uniq –c
```
* Run bowtie2 with a set of single-end reads, reporting up to 5 alignments per read; then determine the number of matches with unmapped mates
* Run bowtie2 with a set of single-end reads, reporting the top 5 alignments for a read; then list the number of matches containing insertions and deletions, respectively
* Run bowtie2 with a set of single-end reads, allowing for local matches; then determine the number of matches with unmapped mates
* Run bowtie2 with a set of single-end reads, reporting the best alignment only; then determine the number of matches on each genomic sequence
```
Answer: Run bowtie2 with a set of single-end reads, reporting the top 5 alignments for a read; then list the number of matches containing insertions and deletions, respectively
```

## Question 9
What does the following snippet of code do NOT do:
```
samtools mpileup –O –f genome.fa  in.bam | cut –f7
```
* Report in the intermediate mpileup output the qualities of all read bases aligned at that position
* Require a sorted BAM file
* Report an empty column
* Produce a 7-column intermediate mpileup file that is piped to ‘cut’
```
Answer: Require a sorted BAM file
```

## Question 10
What does the following code do NOT do:
```
bcftools call –v –c –O z –o out.vcf.gz in.vcf.gz
```
* Report variant sites only
* Call variants in a single sample
* Report output in compressed VCF format
* Skip indels
```
Answer: Skip indels
```
