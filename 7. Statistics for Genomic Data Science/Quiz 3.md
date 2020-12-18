# Module 3 Quiz
```r
library(snpStats)
library(broom)
data(for.exercise)
use <- seq(1, ncol(snps.10), 10)
sub.10 <- snps.10[,use]
snpdata = sub.10@.Data
status = subject.support$cc
```
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
```r
# recode 0 values to NA
snp3 = as.numeric(snpdata[,3])
snp3[snp3==0] = NA

# fit a linear model
lm3 = lm(status ~ snp3)
tidy(lm3)

## # A tibble: 2 x 5
##   term        estimate std.error statistic  p.value
##   <chr>          <dbl>     <dbl>     <dbl>    <dbl>
## 1 (Intercept)   0.544     0.0549     9.91  3.75e-22
## 2 snp3         -0.0394    0.0468    -0.842 4.00e- 1
```
```r
# fit a logistic regression model
glm3 = glm(status ~ snp3,family="binomial")
tidy(glm3)

## # A tibble: 2 x 5
##   term        estimate std.error statistic p.value
##   <chr>          <dbl>     <dbl>     <dbl>   <dbl>
## 1 (Intercept)    0.177     0.220     0.806   0.420
## 2 snp3          -0.158     0.188    -0.841   0.400
```
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
### Answer
```
Linear Model = -0.04

Logistic Model = -0.16

Both models are fit on the additive scale. So in the linear model case, the coefficient is the decrease in probability associated with each additional copy of the minor allele. In the logistic regression case, it is the decrease in the log odds ratio associated with each additional copy of the minor allele.
```

## Question 2
In the previous question why might the choice of logistic regression be better than the choice of linear regression?
```r
par(mfrow=c(1,2))

plot(status ~ snp3,pch=19)
abline(lm3,col="darkgrey",lwd=5)
plot(glm3$residuals)
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%203/Graph2.png)
* It is customary to use logistic regression for case-control data like those obtained from genome-wide association studies.
* If you included more variables it would be possible to get negative estimates for the probability of being a case from the linear model, but this would be prevented with the logistic regression model. 
* The log odds is always more interpretable than a change in probability on the additive scale. 
* The logistic regression model is the natural model for GWAS data. 
### Answer
```
If you included more variables it would be possible to get negative estimates for the probability of being a case from the linear model, but this would be prevented with the logistic regression model. 
```

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
```r
# fit a logistic regression model
snp10 = as.numeric(snpdata[,10])
snp10[snp10==0] = NA
glm10 = glm(status ~ snp10, family="binomial")
tidy(glm10)

## # A tibble: 2 x 5
##   term        estimate std.error statistic p.value
##   <chr>          <dbl>     <dbl>     <dbl>   <dbl>
## 1 (Intercept) -0.00751    0.174    -0.0433   0.965
## 2 snp10        0.00201    0.0933    0.0215   0.983
```
```r
snp10_dom = (snp10 == 2)
glm10_dom = glm(status ~ snp10_dom, family="binomial")
tidy(glm10_dom)

## # A tibble: 2 x 5
##   term          estimate std.error statistic p.value
##   <chr>            <dbl>     <dbl>     <dbl>   <dbl>
## 1 (Intercept)    -0.0339    0.0868    -0.391   0.696
## 2 snp10_domTRUE   0.0643    0.127      0.505   0.614
```

* The recessive model shows a strong effect, but the additive model shows no difference so the recessive model is better. 
* The additive model fits much better since there are fewer parameters to fit and the effect size is so large. 
* No, in all cases, the fitted values are near 0.5 and there are about an equal number of cases and controls in each group. This is true regardless of whether you fit a recessive or additive model. 
* The recessive model fits much better since it appears that once you aggregate the heterozygotes and homozygous minor alleles, there is a bigger difference in the proportion of cases and controls. 
### Answer
```
The recessive model shows a strong effect, but the additive model shows no difference so the recessive model is better. 
```

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
```r
# fit an additive logistic regression model to each SNP
results = rep(NA, dim(snpdata)[2])
for (i in 1:ncol(snpdata)){
  snpdata_i = as.numeric(snpdata[,i])
  snpdata_i[snpdata_i == 0] = NA
  glm_i = glm(status ~ snpdata_i, family = "binomial")
  results[i] = tidy(glm_i)$statistic[2]
}

# average effect size
mean(results)

## ---------------
## [1] 0.007155377
```
```r
# minimum effect size
min(results)

## ---------------
## [1] -4.251469
```
```r
# maximum effect size
max(results)

## ---------------
## [1] 3.900891
```
* Average effect size =  -0.02, minimum =-3.59 , maximum = 4.16
* Average effect size =  1.35, minimum =-6.26 , maximum = 6.26
* Average effect size =  0.007, minimum = -4.25, maximum = 3.90
* Average effect size =  0.02, minimum = -0.88, maximum = 0.88
### Answer
```
Average effect size =  0.007, minimum = -4.25, maximum = 3.90
```

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
```r
# square the coefficients
results_coeff_squre =  results^2

# correlation with the results from using snp.rhs.tests and chi.squared
glm_all = snp.rhs.tests(status ~ 1, snp.data = sub.10)
cor(results_coeff_squre, chi.squared(glm_all))

## ---------------
## [1] 0.9992946
```
* 0.81 They are both testing for the same association using the same additive regression model on the logistic scale. But it doesn't make sense since they should be perfectly correlated. 
* 0.99. They are both testing for the same association using the same additive regression model on the logistic scale. But it doesn't make sense since they should be perfectly correlated. 
* 0.99. They are both testing for the same association using the same additive regression model on the logistic scale but using slightly different tests. 
* 0.99. It doesn't make sense since they are both testing for the same association using the same additive regression model on the logistic scale but using slightly different tests. 
### Answer
```
0.99. They are both testing for the same association using the same additive regression model on the logistic scale but using slightly different tests.
```

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
```r
 library(devtools)
 library(Biobase)
 library(limma)
 library(edge)
 library(genefilter)
 
edata = log2(as.matrix(edata) + 1)

# perform rowttests
tstats_obj = rowttests(edata, as.factor(pdata$population))
tidy(tstats_obj)

## # A tibble: 3 x 13
##   column     n   mean    sd   median trimmed     mad       min   max range
##   <chr>  <dbl>  <dbl> <dbl>    <dbl>   <dbl>   <dbl>     <dbl> <dbl> <dbl>
## 1 stati… 12984 -3.43  3.88  -2.84    -3.16   2.94    -2.31e+ 1  8.31 31.5 
## 2 dm     52580 -0.129 0.372  0       -0.0283 0       -4.37e+ 0  1.51  5.89
## 3 p.val… 12984  0.168 0.266  0.00441  0.109  0.00441  2.23e-47  1.00  1.00
## # … with 3 more variables: skew <dbl>, kurtosis <dbl>, se <dbl>
```
```r
# perform rowFtests
fstats_obj = rowFtests(edata, as.factor(pdata$population))
tidy(fstats_obj)

## # A tibble: 2 x 13
##   column     n   mean     sd  median trimmed     mad      min    max  range
##   <chr>  <dbl>  <dbl>  <dbl>   <dbl>   <dbl>   <dbl>    <dbl>  <dbl>  <dbl>
## 1 stati… 12984 26.8   39.5   8.40     18.4   8.20    3.39e- 7 535.   535.  
## 2 p.val… 12984  0.168  0.266 0.00441   0.109 0.00441 2.23e-47   1.00   1.00
## # … with 3 more variables: skew <dbl>, kurtosis <dbl>, se <dbl>
```
```r
par(mfrow=c(1,2))
hist(tstats_obj$statistic, col=2)
hist(fstats_obj$statistic, col=2)
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%203/Graph3.png)
* You get the same p-value but different statistics. This is because the F-statistic and t-statistic test the same thing when doing a two group test and one is a transform of the other. 
* You get different p-values and statistics. The F-statistic and t-statistic are testing the same thing but do it totally differently. 
* You get the same p-values and statistics. This is because the F-statistic and t-statistic are the exact same in this case. 
* You get different p-values but the same statistic. This is because the F-statistic and t-statistic test the same thing when doing a two group test and one is a transform of the other. 
### Answer
```
You get the same p-value but different statistics. This is because the F-statistic and t-statistic test the same thing when doing a two group test and one is a transform of the other.
```

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
```r
library(DESeq2)
library(limma)
library(edge)
library(genefilter)
```
```r
# using DESeq2 test the differences between the studies
de = DESeqDataSetFromMatrix(edata, pdata, ~study)
glm_de = DESeq(de)
result_de = results(glm_de)

# using limma test the differences
edata = log2(as.matrix(edata) + 1)
mod = model.matrix(~ as.factor(pdata$study))
fit_limma = lmFit(edata, mod)
ebayes_limma = eBayes(fit_limma) 
top = topTable(ebayes_limma,number=dim(edata)[1], sort.by="none")

# correlation in the statistics between two analyses
cor(result_de$stat, top$t)

## -------------
## [1] 0.9278568
```

```r
# make an MA-plot
y = cbind(result_de$stat, top$t)
limma::plotMA(y)
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%203/Graph4.png)
* 0.85. There are more differences for the large statistics.
* 0.93. There are more differences for the small statistics. 
* 0.63. There are more differences for the large statistics.
* 0.93. There are more differences for the large statistics.
### Answer
```
0.93. There are more differences for the large statistics.
```

## Question 8
Apply the Benjamni-Hochberg correction to the P-values from the two previous analyses. How many results are statistically significant at an FDR of 0.05 in each analysis? 
```r
# DESeq analysis
fp_bh = p.adjust(result_de$pvalue, method="BH")
sum(fp_bh < 0.05)

## --------
## [1] 1995
```
```r
# limma analysis
fp_bh = p.adjust(top$P.Value, method="BH")
sum(fp_bh < 0.05)

## --------
## [1] 2807

```
* DESeq = 1119 significant; 

  limma = 2328 significant
* DESeq = 12 significant; 

  limma = 3significant
* DESeq = 1995 significant; 

  limma = 2807 significant
* DESeq = 0 significant; 

  limma = 0 significant
### Answer
```
DESeq = 1995 significant; 

limma = 2807 significant
```

## Question 9
Is the number of significant differences surprising for the analysis comparing studies from Question 8? Why or why not? 
* Yes. This is a very large number of genes different between studies and we don't have a good explanation.
* No. There are very few genes different between studies and that is what we would expect. 
* Yes and no. It is surprising because there is a large fraction of the genes that are significantly different, but it isn't that surprising because we would expect that when comparing measurements from very different batches. 
* Yes and no. It is surprising because there very few genes that are significantly different, but it isn't that surprising because we would expect that when comparing measurements from very different batches.
### Answer
```
Yes and no. It is surprising because there is a large fraction of the genes that are significantly different, but it isn't that surprising because we would expect that when comparing measurements from very different batches. 
```

## Question 10
Suppose you observed the following P-values from the comparison of differences between studies. Why might you be suspicious of the analysis? 
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%203/Graph1.png)
* This p-value histogram appears correct in the case where there is a large number of statistically significant results. 
* The p-values should be uniformly distributed, but here they are not uniformly distributed. 
* The p-values should have a spike near zero (the significant results) and be flat to the right hand side (the null results) so the distribution pushed toward one suggests conservative p-value calculation.
* There are too many small p-values so there are too may statistically significant results. 
### Answer
```
The p-values should have a spike near zero (the significant results) and be flat to the right hand side (the null results) so the distribution pushed toward one suggests conservative p-value calculation.
```
