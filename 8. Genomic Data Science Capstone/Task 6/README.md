# Peer-graded Assignment: Statistical Analysis

## Instructions
The next step is to perform a statistical analysis to detect genes that are differentially expressed. 
To do this, set up the null and alternative hypotheses. Be sure to identify which covariates you are going to adjust for in your analysis. 
Then use a linear model to test for genes that are differentially expressed between age groups adjusting for an appropriate set of covariates. 
You can use one of several packages (DESeq, edgeR, limma+voom, or edge) to perform this analysis. 
Use a correction to identify genes that are differentially expressed after accounting for multiple testing. 
Make a plot of the fold change (or effect size) for age in each linear model versus the log10 p-value. 
This is called a [volcano plot](https://www.r-bloggers.com/2014/05/using-volcano-plots-in-r-to-visualize-microarray-and-rna-seq-results/) which you can use to see if there are any major patterns among the observed differential expression.

## Review criteria
Upload a tab-delimited file with three columns - gene name, fold-change estimates, the p-value for that gene, and the adjusted p-value

* Does the file have gene names, fold-change estimates,  p-values and adjusted p-values?
* Do the p-values seem appropriate?
* Upload a PDF document describing your analysis and your results, including how many genes were differentially expressed at a given error rate, and a volcano plot of the results.

* Does the document have the required components (description of analysis and volcano plot)?
* Does the results seems justified?
