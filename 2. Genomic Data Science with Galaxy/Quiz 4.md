# Module 3 Quiz

## Question 1
What does it mean to align-then-assemble?
* Align and assemble existing reference genomes.
* Assemble transcripts, and then align transcripts to an existing genome.
* Align reads to an existing reference genome, and then assemble transcripts from the spliced alignments.
* Align existing reference genomes, and then assemble the reads.
```
Answer: Align reads to an existing reference genome, and then assemble transcripts from the spliced alignments.
```

## Question 2
Which of the following statements is FALSE?
* De-novo assembly is more computationally intensive than align-then-assemble.
* Align-then-assemble approach is potentially more sensitive.
* De-novo assembly is not robust to variation
* Align-then-assemble is not robust to variation
```
Answer: Align-then-assemble is not robust to variation.
```

## Question 3
What of following formats can tophat results produce?

A) BED format.

B) ADAM format.

C) BAM format.

* A and C
* B and C
* B
* C
```
Answer: A and C
```

## Question 4
Which tool in the cufflinks suite is used to find the differentially expressed genes?
* Cuffmerge
* Cufflinks
* Cuffquant
* Cuffdiff
```
Answer: Cuffdiff
```

## Question 5
One of the options is NOT a column in the output produced by Cuffdiff.
* gene name and gene ID
* q_value
* log2 (fold change)
* Length of the differentially expressed gene
```
Answer: Per sequence base quality
```

## Question 6
What is the main purpose of Cuffmerge and what is its input format?
* To merge different Cufflinks assemblies and SAM files.
* To find differentially expressed genes and BED files
* To merge different Cufflinks assemblies and BED files
* To merge different Cufflinks assemblies together and GTF files.
```
Answer: To merge different Cufflinks assemblies together and GTF files.
```

## Question 7
Can we use Galaxy to run the same tophat (or other tool) job over Multiple datasets?
* Yes, but the datasets need to be of the same format.
* No, this is not supported, yet.
* Yes, but not with all tools.
* Yes, the datasets need to be of the format the tool can take as input.
```
Answer: Yes, the datasets need to be of the format the tool can take as input.
```

## Question 8
What Galaxy tool might we use to refine our Cuffdiff output to show only differentially expressed genes?
* Cufflinks
* Select random lines
* Filter
* Cuffmerge
```
Answer: Filter
```

## Question 9
What comes after mapping the RNA seq data to a reference genome?
* Using a reference annotation we continue to do differential expression analysis using the Cufflinks suite.
* Remap the reads using TopHat and continue to do differential expression analysis using the Cufflinks suite.
* Compare the reference annotation with the reference genome.
* QC again to make sure we have mapped correctly.
```
Answer: Remap the reads using TopHat and continue to do differential expression analysis using the Cufflinks suite.
```

## Question 10
What is the idea behind setting the tool form “Use Reference Annotation” to “reference annotation as guide” in Cufflinks?

A) Tells Cufflinks to use the reference annotation to guide the assembly.

B) Results will contain referenced transcripts, novel genes and isoforms.

C) Tells Cufflinks to remove all unannotated transcripts.
* B
* A and B
* B and C
* C
```
Answer: A and B
```

## Question 11
What does the “log2(fold change)” in the gene differential expression testing result mean?

A) Its the log-ratio of FPKM values for a pair of expressed genes.

B) Its the log-ratio between mapped and unmapped reads.

C) It indicates genes with significantly different expression profiles.
* A
* A and C
* B
* A and B
```
Answer:  A and C
