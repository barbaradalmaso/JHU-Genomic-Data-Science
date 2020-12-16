# Module 2 Quiz

## Question 1
Which of the following strings cannot denote a DNA sequence:
* AGCTACTACGAGCT
* CCCCCCCCCC
* AAAAAAAAA
* APCTSYFPEITHI

## Question 2
How many lines does it take to specify:

i) one fasta sequence? and ii) one fastq sequence?

Select the best answer.

* Fasta – a fasta header followed by any number of sequence lines; fastq – 4 lines
* Fasta – any number of lines, including a fasta header; fastq – 2 lines
* Fasta – 100 lines; fastq – 2 lines
* Fasta – 1 line; fastq – 4 lines

## Question 3
Which of the following is incorrect:
* The length of a read with CIGAR 51M1D24M is 75 bp.
* ‘SRA” stands for “Short Read Archive”, an NCBI database that stores short read sequences.
* An unmapped read can be represented as a SAM record with a ‘*’ in column 7.
* BEDtools can be used to align sequences to the genome.

## Question 4
Which of the following is NOT an alignment operation:
* Substitution
* Insertion
* Deletion
* Cut and paste

## Question 5
What is the minimum number of columns that are sufficient to specify a BED format?
* 3
* 9
* 8
* 12

## Question 6
Which of the following represents the most accurate conversion into BED of the GTF record:
```
chr1  CLASS exon  516 811 100 + . gene_id “genA”; 
    transcript_id “genA.1”;
chr1  CLASS exon  1001  1115  100 + . gene_id 
    “genA”; transcript_id “genA.1”;
chr1  CLASS exon  3010  3312  100 + . gene_id 
    “genA”; transcript_id “genA.1”
```
* 
```
chr1  515 3312  genA.1  100 + 515 3312  0 3 296
    ,115,303  0,485,2494
```
*
```
chr1 516 3312 genA + 516 3312 0 2 296,303 0,2494
```
*
```
chr1  516 3312  genA.1  100 + 800 900 0 3 296,115
    ,303  0,485,2494  
```
*
```
chr1 515 811 genA 100 + . 800 811 0 1 296 0
```

## Question 7
Determine the number of genes, transcripts, exons per transcript, gene orientation (strand), and the length of 5’ most exon(s) from the GTF snippet below. Select the correct answer.
```
chr1  HAVANA  gene  3205901 3671498 . - . gene_id 
    "MUSG51951.5"; 
chr1  HAVANA  transcript  3205901 3216344 . - . gene_id 
    "MUSG51951.5"; transcript_id "MUST162897.1"; 
chr1  HAVANA  exon  3213609 3216344 . - . gene_id 
    "MUSG51951.5"; transcript_id "MUST162897.1”;
chr1  HAVANA  exon  3205901 3207317 . - . gene_id 
    "MUSG51951.5"; transcript_id "MUST162897.1
chr1  HAVANA  transcript  3206523 3215632 . - . gene_id 
    "MUSG51951.5"; transcript_id "MUST159265.1”;
chr1  HAVANA  exon  3213439 3215632 . - . gene_id 
    "MUSG51951.5"; transcript_id "MUST159265.1";
chr1  HAVANA  exon  3206523 3207317 . - . gene_id 
    "MUSG51951.5"; transcript_id "MUST159265.1”;
```
* Genes: 1; Transcripts: 2; Exons: 2,2; Strand: -; Length of 5’ exon(s): 2736, 2194.
* Genes: 2; Transcripts: 2; Exons: 3,2; Strand: -; Length of 5’ exon(s): 2736, 2194.
* Genes: 2; Transcripts: 2; Exons: 2,2; Strand: -; Length of 5’ exon(s): 2500, 2000.
* Genes: 2; Transcripts: 4; Exons: 1,1,1,1; Strand: -; Length of 5’ exon(s): 2736,1417, 2194,795.

## Question 8
Which of the following is FALSE for the following read alignments:
```
R1  83  chr12 9232390 255 50M = 9232180 0 
ATGGCAGAGCCTAATATGTCTCCTAGAGAATGGGAGAGATGGGAAGTCAT  
    HGHHHHHHHHHHHHHHHHHHHHHHHHHHIGIIIIHHHHHHHHHHHGHHFH  NM:i:0  
    NH:i:1  HI:i:0
R2  97  chr12 9232391 255 28M278N22M  = 9242529
0 TGGCAGAGCCTAATATGTCTCCCAAAACTGAGACAGAAGCTCGGGCAGAT  D
    >DDDHHHHHHHHHHIHIHHHHHIHHHHIGFFGGGHHHHHHHHHHFB.F  NM:i:4  NH
    :i:3  HI:i:0  XS:A:+  NS:i:2
R3  77  * 0 0 0 * * 0 0 
    CTGATATGAGGAAAGAGGATTGCTTAAGCCCAGGAGGTAGAGGCTGTACC  
    @@@FFDFFHFFHHJJJJIJEGFGIGHHIHIIIIGCDE?D?FGGCBHDGGG
```
* R2 maps in 3 places within the genome.
* R1 has an exact match to the genome.
* R2 has an exact match to the genome.
* R1, R2 and R3 all have length 50.

## Question 9
For the alignment below, which statements are FALSE? The binary encoding for 97 is 972 = 0000 0110 00012. Select all answers that apply.
```
R2  97  chr12 9232391 255 28M278N22M  = 9242529
0 TGGCAGAGCCTAATATGTCTCCCAAAACTGAGACAGAAGCTCGGGCAGAT  D
    >DDDHHHHHHHHHHIHIHHHHHIHHHHIGFFGGGHHHHHHHHHHFB.F  NM:i:4  XS
    :A:+  NS:i:2
```
* The read matches to the genome with 4 differences.
* The sequence of the read’s mate is reverse complemented in its alignment.
* The alignment represents a potential PCR or optical duplicate.
* The alignment passes quality checks.
* The two mates are identical in sequence.
* Both the read and its mate are mapped.

## Question 10
Files ‘A.bed’ and ‘B.bed’ contain the following sets of intervals:
```
File A            File B
chr1  100 400       chr1  300 500
chr1  1000  1400        chr1  900 1600
chr1  2000  2400        chr12 2000  2200
```
What would be the answers for the following sequence of commands: 
```
bedtools intersect –wao –a A.bed –b B.bed | sort –u | wc -l
bedtools intersect –wo –a A.bed –b B.bed  | cut –f1-3 | sort –u 
    | wc -l
bedtools intersect –wo –a A.bed -b B.bed  | cut -f4-6 | sort –u 
    | wc -l
```
* 5, 5, 5
* 3, 4, 2
* 9 , 2, 2
* 3, 2, 2
