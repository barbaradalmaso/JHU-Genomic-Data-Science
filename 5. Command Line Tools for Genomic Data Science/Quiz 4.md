# Module 4 Quiz

## Question 1
Which of the following is FALSE:
* Alternative splicing is a common phenomenon in both animals and plants.
* A human gene can express at most 12 splice variants.
* A codon is a nucleotide triplet that is translated into one amino acid.
* The coding region with a protein-coding gene is used as the template for forming a protein.

```
Answer: A human gene can express at most 12 splice variants.
```

## Question 2
Which of the following is FALSE about the organization of a eukaryotic gene:
* Genes that have only one exon are not alternatively spliced.
* The number of introns in a transcript is one less than the number of exons.
* Some eukaryotic gene transcripts can consist of a single exon.
* The length of an intron cannot be a multiple of 3.
```
Answer: The length of an intron cannot be a multiple of 3.
```

## Question 3
What programs could you use to align RNA-seq reads to: i) a reference genome, and ii) a transcript database?
* tophat, bowtie
* bowtie, tophat
* bowtie, bowtie
* bowtie, samtools
```
Answer: tophat, bowtie
```

## Question 4
Which of the following is FALSE:
* RNA-seq analyses can reveal known genes and their splice variants, as well as novel genes.
* Unspliced reads can be used to determine the introns of a gene.
* ‘Transfrag’ stands for ‘transcript fragments’, a reference to the fact than transcript assemblers cannot always reconstruct full-length splice variants.
* The sums of FPKMs of all transcripts of a gene is equal to the gene’s expression level.
```
Answer: Unspliced reads can be used to determine the introns of a gene.
```

## Question 5
What programs could be used to: i) assemble transcripts from RNA-seq reads, and ii) identify potentially novel transcripts and genes
* cuffcompare, cuffcompare
* cufflinks, cuffdiff
* cufflinks, cuffcompare
* cufflinks, tophat
```
Answer: cufflinks, cuffcompare
```

## Question 6
Which of the following is FALSE about the gene annotations in the following GTF snippet:
```
chr1  MGF gene  3413609 3671498 . - . gene_id 
    "MG051951";
chr1  MGF transcript  3413609 3416344 . - .gene_id 
    "MG051951"; transcript_id "MT162897";
chr1  MGF exon  3413609 3416344 . - . gene_id 
    "MG051951"; transcript_id "MT162897";
chr1  MGF transcript  3421702 3671498 . - . gene_id 
    "MG051951"; transcript_id "MT070533";
chr1  MGF exon  3670552 3671498 . - . gene_id 
    "MG051951"; transcript_id "MT070533";
chr1  MGF CDS 3670552 3671348 . - 0 gene_id "MG051951"; 
    transcript_id "MT070533";
chr1  MGF exon  3421702 3421901 . - . gene_id 
    "MG051951"; transcript_id "MT070533";
chr1  MGF CDS 3421792 3421901 . - 1 gene_id "MG051951"; 
    transcript_id "MT070533";
```
* The two transcripts for gene MG051951 overlap on the genome.
* It contains only one gene, MG051951.
* Gene MG051951 has two transcripts, MT162897 and MT070533.
* Transcript MT162897 has a single exon.
```
Answer: The two transcripts for gene MG051951 overlap on the genome.
```

## Question 7
What does the following code NOT do:
```
BWT2IDX=/home/me/genomes/hg20/hg20
ANNOT=/home/me/genomes/hg20/myannot.gtf
ANNOTIDX=/home/me/genomes/hg20/myannot/myannot
mkdir -p /home/me/SRR100000
tophat2 -o /home/me/SRR100000 -p 10 --max-multihits 10 \
        -r 26 –-mate-std-dev 25 \
        -a 6 \
        -G $ANNOT –-transcriptome-index $ANNOTIDX \
        $BWT2IDX \
        /home/me/SRR100000_1.fastq.gz /home/me/SR100000_2.fastq
            .gz
```
* Report spliced reads with at most 6 mismatches in the anchor site
* Create the output in the /home/me/SRR100000 directory
* Run multi-threaded, with 10 threads
* Report only reads with 10 or fewer alignments on the genome
```
Answer: Report spliced reads with at most 6 mismatches in the anchor site
```

## Question 8
What does the following code NOT do:
```
TOPHATDIR=/home/florea/Tophat/
mkdir –p Test1
cd Test1
ln –s $TOPHATDIR/accepted_hits.bam .
cufflinks -L Test1 -p 8 –j 0.10 –F 0.05 accepted_hits.bam
```
* Use the default reference transcript annotation to guide assembly
* Generate output in the ./Test1 subdirectory
* Create the subdirectory Test1, if it does not already exist
* After creating the directory Test1, make it the current directory
```
Answer: Use the default reference transcript annotation to guide assembly
```

## Question 9
Which of the following is NOT described in the following summary file produced by tophat:
```
Left reads:
          Input     :  60586968
           Mapped   :  58163843 (96.0% of input)
            of these:   6832240 (11.7%) have multiple alignments 
                (359075 have >10)
Right reads:
          Input     :  60586968
           Mapped   :  56969290 (94.0% of input)
            of these:   6668479 (11.7%) have multiple alignments 
                (358573 have >10)
95.0% overall read mapping rate.
Aligned pairs:  55880048
     of these:   6491876 (11.6%) have multiple alignments
                 2795712 ( 5.0%) are discordant alignments
87.6% concordant pair alignment rate.
```
* The reads were 100 bp long
* Tophat was run with paired-end data
* There were 121,173,936 reads total in the input set
* 96.0% of the mate 1 reads could be mapped
```
Answer: The reads were 100 bp long
```

## Question 10
Which of the following is NOT TRUE about the output below, obtained from a cuffdiff differential expression analysis:
```
XLOC_000002 XLOC_000002 AT1G01020 1:5927-8737 q1  q2  OK  1
    .13032  3.48406 1.62404 0.694576  0.5277  0.998846  no
XLOC_000004 XLOC_000004 AT1G01073 1:44676-44787 q1  q2  
    NOTEST  0 0 0 0 1 1 no
XLOC_000042 XLOC_000042 AT1G01580 1:209394-213041 q1  q2  OK  1
    .59512  0 -inf  nan 5e-05 0.0096703 yes
```
* There are not enough alignments for testing for differential expression at locus XLOC_000004
* There are too many alignments for testing for differential expression at locus XLOC_000004
* Locus XLOC_000042 corresponds to gene AT1G01580
* Locus XLOC_000004 corresponds to gene AT1G01073
```
Answer: There are too many alignments for testing for differential expression at locus XLOC_000004
```
