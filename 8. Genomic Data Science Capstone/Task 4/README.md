# Peer-graded Assignment: Get Feature Counts

## Instructions
Now that you have performed alignment and quality control, the next step is to calculate the abundance of every gene in every sample. This count is an approximation to the expression level for the gene. It is calculated by comparing the aligned reads to pre-specified positions in the genome that correspond to known genes. To calculate these counts you need a file that tells you the positions of the genes. You will need the “gtf file” describing the locations of the genes for the corresponding genome you aligned to during the alignment step. You can then use one of many types of software for obtaining the gene counts (featureCounts, HTseq, etc). The result should be a table that is formatted with one gene per row and one sample per column. The count for that gene in that sample is in the corresponding cell.  

## Review Criteria
Upload the gene expression table in a tab-delimited text file 

* Is there a tab delimited file with the gene expression counts for each sample?
* Do the counts appear to be appropriate ?(you may have to download the file and make some plots)
