# Module 3 Quiz

## Question 1
Load the example SNP data with the following code:
```r
library(snpStats)
library(broom)
data(for.exercise)
use <- seq(1, ncol(snps.10), 10)
sub.10 <- snps.10[,use]
snpdata = sub.10@.Data
status = subject.support$cc
```
Fit a linear model and a logistic regression model to the data for the 3rd SNP. What are the coefficients for the SNP variable? How are they interpreted? (Hint: Don't forget to recode the 0 values to NA for the SNP data)
* Linear Model = -0.04

  Logistic Model = -0.16

  Both models are fit on the additive scale. So in the linear model case, the coefficient is the decrease in probability associated with each additional copy of the minor allele. In the logistic regression case, it is the decrease in the log odds ratio associated with each additional copy of the minor allele. 
* Linear Model =  -0.16

  Logistic Model = -0.04

  Both models are fit using a dominance model. So in the linear model case, the coefficient is the decrease in probability associated with one copy of the minor allele. In the logistic regression case, it is the decrease in the log odds ratio associated with one copy of the minor allele. 
* Linear Model = -0.04

  Logistic Model = -0.16

  Both models are fit on the additive scale. So in both cases the coefficient is the decrease in probability associated with each additional copy of the minor allele.
* Linear Model = 0.54

  Logistic Model = 0.18

  Both models are fit on the additive scale. So in both cases the coefficient is the decrease in probability associated with each additional copy of the minor allele.

## Question 2
In the previous question why might the choice of logistic regression be better than the choice of linear regression?
* It is customary to use logistic regression for case-control data like those obtained from genome-wide association studies.
* If you included more variables it would be possible to get negative estimates for the probability of being a case from the linear model, but this would be prevented with the logistic regression model. 
* The log odds is always more interpretable than a change in probability on the additive scale. 
* The logistic regression model is the natural model for GWAS data. 

## Question 3
Load the example SNP data with the following code:
```r
library(snpStats)
library(broom)
data(for.exercise)
use <- seq(1, ncol(snps.10), 10)
sub.10 <- snps.10[,use]
snpdata = sub.10@.Data
status = subject.support$cc
```
Fit a logistic regression model on a recessive (need 2 copies of minor allele to confer risk) and additive scale for the 10th SNP. Make a table of the fitted values versus the case/control status. Does one model fit better than the other?
* The recessive model shows a strong effect, but the additive model shows no difference so the recessive model is better. 
* The additive model fits much better since there are fewer parameters to fit and the effect size is so large. 
* No, in all cases, the fitted values are near 0.5 and there are about an equal number of cases and controls in each group. This is true regardless of whether you fit a recessive or additive model. 
* The recessive model fits much better since it appears that once you aggregate the heterozygotes and homozygous minor alleles, there is a bigger difference in the proportion of cases and controls. 

## Question 4
Load the example SNP data with the following code:
```r
library(snpStats)
library(broom)
data(for.exercise)
use <- seq(1, ncol(snps.10), 10)
sub.10 <- snps.10[,use]
snpdata = sub.10@.Data
status = subject.support$cc
```
Fit an additive logistic regression model to each SNP. What is the average effect size? What is the max? What is the minimum?
* Average effect size =  -0.02, minimum =-3.59 , maximum = 4.16
* Average effect size =  1.35, minimum =-6.26 , maximum = 6.26
* Average effect size =  0.007, minimum = -4.25, maximum = 3.90
* Average effect size =  0.02, minimum = -0.88, maximum = 0.88

## Question 5
Load the example SNP data with the following code:
```r
library(snpStats)
library(broom)
data(for.exercise)
use <- seq(1, ncol(snps.10), 10)
sub.10 <- snps.10[,use]
snpdata = sub.10@.Data
status = subject.support$cc
```
Fit an additive logistic regression model to each SNP and square the coefficients. What is the correlation with the results from using 
```snp.rhs.tests``` and ```chi.squared?``` Why does this make sense?
* 0.81 They are both testing for the same association using the same additive regression model on the logistic scale. But it doesn't make sense since they should be perfectly correlated. 
* 0.99. They are both testing for the same association using the same additive regression model on the logistic scale. But it doesn't make sense since they should be perfectly correlated. 
* 0.99. They are both testing for the same association using the same additive regression model on the logistic scale but using slightly different tests. 
* 0.99. It doesn't make sense since they are both testing for the same association using the same additive regression model on the logistic scale but using slightly different tests. 

## Question 6
Load the Montgomery and Pickrell eSet:
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/montpick_eset.RData")
load(file=con)
close(con)
mp = montpick.eset
pdata=pData(mp)
edata=as.data.frame(exprs(mp))
fdata = fData(mp)
```
Do the log2(data + 1) transform and fit calculate F-statistics for the difference between studies/populations using genefilter:rowFtests and using genefilter:rowttests. Do you get the same statistic? Do you get the same p-value?
* You get the same p-value but different statistics. This is because the F-statistic and t-statistic test the same thing when doing a two group test and one is a transform of the other. 
* You get different p-values and statistics. The F-statistic and t-statistic are testing the same thing but do it totally differently. 
* You get the same p-values and statistics. This is because the F-statistic and t-statistic are the exact same in this case. 
* You get different p-values but the same statistic. This is because the F-statistic and t-statistic test the same thing when doing a two group test and one is a transform of the other. 

## Question 7
Load the Montgomery and Pickrell eSet:
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/montpick_eset.RData")
load(file=con)
close(con)
mp = montpick.eset
pdata=pData(mp)
edata=as.data.frame(exprs(mp))
edata = edata[rowMeans(edata) > 100,]
fdata = fData(mp)
```
First test for differences between the studies using the ```DESeq2```
package using the ```DESeq``` function. Then do the log2(data + 1) transform and do the test for differences between studies using the 
```limma``` package and the ```lmFit```, ```ebayes``` and ```topTable``` functions. What is the correlation in the statistics between the two analyses? Are there more differences for the large statistics or the small statistics (hint: Make an MA-plot).
* 0.85. There are more differences for the large statistics.
* 0.93. There are more differences for the small statistics. 
* 0.63. There are more differences for the large statistics.
* 0.93. There are more differences for the large statistics.

## Question 8
Apply the Benjamni-Hochberg correction to the P-values from the two previous analyses. How many results are statistically significant at an FDR of 0.05 in each analysis? 
* DESeq = 1119 significant; 

  limma = 2328 significant
* DESeq = 12 significant; 

  limma = 3significant
* DESeq = 1995 significant; 

  limma = 2807 significant
* DESeq = 0 significant; 

  limma = 0 significant

## Question 9
Is the number of significant differences surprising for the analysis comparing studies from Question 8? Why or why not? 
* Yes. This is a very large number of genes different between studies and we don't have a good explanation.
* No. There are very few genes different between studies and that is what we would expect. 
* Yes and no. It is surprising because there is a large fraction of the genes that are significantly different, but it isn't that surprising because we would expect that when comparing measurements from very different batches. 
* Yes and no. It is surprising because there very few genes that are significantly different, but it isn't that surprising because we would expect that when comparing measurements from very different batches.

## Question 10
Suppose you observed the following P-values from the comparison of differences between studies. Why might you be suspicious of the analysis? 
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%203/Graph1.png)
* This p-value histogram appears correct in the case where there is a large number of statistically significant results. 
* The p-values should be uniformly distributed, but here they are not uniformly distributed. 
* The p-values should have a spike near zero (the significant results) and be flat to the right hand side (the null results) so the distribution pushed toward one suggests conservative p-value calculation.
* There are too many small p-values so there are too may statistically significant results. 
