# Module 4 Quiz

## Question 1
Which of the following is FALSE:
* One type of alternative splicing event is exon skipping, where an internal exon may be missing from some transcripts of a gene and present in others.
* The spliceosome undertakes splicing, or the removal of introns and joining of exons, to form an mRNA.
* Genes contain one long untranslated region surrounded by two terminal coding regions.
* Alternative splicing can create multiple protein and/or mRNA isoforms from the same gene.

## Question 2
Which of the following is FALSE about the organization of a eukaryotic gene:
* Genes that have only one exon are not alternatively spliced.
* The number of introns in a transcript is one less than the number of exons.
* Some eukaryotic gene transcripts can consist of a single exon.
* The length of an intron cannot be a multiple of 3.

## Question 3
What programs could you use to align RNA-seq reads to: i) a reference genome, and ii) a transcript database?
* tophat, igv
* tophat, bcftools
* tophat, bedtools
* tophat, bwa

## Question 4
Which of the following is FALSE:
* RNA-seq analyses can reveal known genes and their splice variants, as well as novel genes.
* Unspliced reads can be used to determine the introns of a gene.
* ‘Transfrag’ stands for ‘transcript fragments’, a reference to the fact than transcript assemblers cannot always reconstruct full-length splice variants.
* The sums of FPKMs of all transcripts of a gene is equal to the gene’s expression level.

## Question 5
What programs could be used to: i) assemble transcripts from RNA-seq reads, and ii) identify potentially novel transcripts and genes
* cuffcompare, cuffcompare
* cufflinks, cuffdiff
* cufflinks, cuffcompare
* cufflinks, tophat

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
* The gene spans the interval chr1:3413609-3671498.
* Transcript MT070533 has 4 exons.
* Transcript MT162897 is located on the reverse strand.
* The 3’ UTR of transcript MT070533 is located at positions chr1:3421702-3421791

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
* Take input data stored in the /home/me directory
* Take compressed input data
* Align paired-end data
* Report only the top 10 alignments for each read

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
* Locus XLOC_000042 is novel 
* The p-value for the t-test at locus XLOC_000002 is 0.5277
* Locus XLOC_000002 is not significantly differentially expressed between the conditions
* The q-value, or false discovery rate (FDR), at locus XLOC_000002 is 0.998846
