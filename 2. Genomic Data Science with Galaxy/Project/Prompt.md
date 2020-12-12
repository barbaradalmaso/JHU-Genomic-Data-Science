## Prompt

Use the text box below to submit a short write-up describing your results including the information requested above. (Maximum 300 words)
```
Answer: 

Briefly, analysis included quality control of the reads, alignment and finally variant calling and annotation of the varians. All three samples were analysed together in the end as a batch. The alignment of the reads was made against the hg19 genome assembly and the resulting BAM files were used as input for FreeBayes variant caller tool. Annotation and filltering only for the statistically signiticant variants of the VCF file gave the following results:

The analysis resulted in 2548 statistically significant(QUAL>50, Phred scaled score) variant sites, of which:
(1) 2243 are SNPs,
(2) 243 insertions/deletions; and
(3) 68 MNPs.

Of all the variant sites:
(4) 2445 have at least 2 alternate alleles.

Among the 236 genes that were found having variant sites, the following five seem to have largest number: 
a) RBFOX1; b) LMF1; c) ABAT; d)CACNA1H; and e) ADCY9.

```
