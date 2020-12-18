# Module 2 Quiz
```r
library(ballgown)
library(Biobase)
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/montpick_eset.RData")
load(file=con)
close(con)
mp = montpick.eset
pdata=pData(mp)
edata=as.data.frame(exprs(mp))
fdata = fData(mp)
```

## Question 1
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
1. Do no transformations?

2. log2(data + 1) transform?

3. log2(data + 1) transform and subtract row means?
```r
# No transformations
svd1 = svd(edata)
ori_pca = svd1$d^2/sum(svd1$d^2)
ori_pca[1]

##   -------
## [1] 0.8873421
```
```r
# log2 transform
edata_log2 = log2(edata + 1)
svd2 = svd(edata_log2)
log2_pca = svd2$d^2/sum(svd2$d^2)
log2_pca[1]

##   -------
## [1] 0.9737781
```
```r
# log2 transform, subtract row means
edata_centered = edata_log2 - rowMeans(edata_log2)
svd3 = svd(edata_centered)
centered_data_pca = svd3$d^2/sum(svd3$d^2)
centered_data_pca[1]

##   -------
## [1] 0.3463729
```
* a. 0.89 b. 0.97 c. 0.35
* a. 0.97 b. 0.97 c. 0.97
* a. 0.97 b. 0.97 c. 0.35
* a. 0.89 b. 0.89 c. 0.35
### Answer
```
a. 0.89 b. 0.97 c. 0.35
```

## Question 2
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
Perform the log2(data + 1) transform and subtract row means from the samples. Set the seed to 
```333``` and use k-means to cluster the samples into two clusters. Use 
```svd``` to calculate the singular vectors. What is the correlation between the first singular vector and the sample clustering indicator?
```r
edata_log2 = log2(edata + 1)
edata_centered = edata_log2 - rowMeans(edata_log2)

# use svd to calculate the singular vectors
set.seed(333)
svd1 = svd(edata_centered)

edata_kmeans = kmeans(t(edata_centered), centers=2)
cor.test(svd1$v[,1], edata_kmeans$cluster)

## 
##  Pearson's product-moment correlation
## 
## data:  svd1$v[, 1] and edata_kmeans$cluster
## t = -19.683, df = 127, p-value < 2.2e-16
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.9049326 -0.8176191
## sample estimates:
##        cor 
##   -------
## -0.8678247
```
* 0.87
* -0.52
* 0.33
* 0.85
### Answer
```
0.87
```

## Question 3
Load the Bodymap data with the following command
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bodymap_eset.RData")
load(file=con)
close(con)
bm = bodymap.eset
edata = exprs(bm)
pdata_bm=pData(bm)
```
Fit a linear model relating the first gene’s counts to the number of technical replicates, treating the number of replicates as a factor. Plot the data for this gene versus the covariate. Can you think of why this model might not fit well?
```r
# fit linear model
lm1 = lm(edata[1,] ~ pdata_bm$num.tech.reps)

# plot the data
plot(pdata_bm$num.tech.reps,edata[1,])
abline(lm1$coeff[1], lm1$coeff[2], col=2, lwd=3)
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%202/Graph1.png)

* There are very few samples with more than 2 replicates so the estimates for those values will not be very good. 
* The difference between 2 and 5 technical replicates is not the same as the difference between 5 and 6 technical replicates. 
* The variable ```num.tech.reps``` is not a good measure of the technical variability in the data.
* There may be different numbers of counts for different numbers of technical replicates. 
### Answer
```
There are very few samples with more than 2 replicates so the estimates for those values will not be very good.
```

## Question 4
Load the Bodymap data with the following command
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bodymap_eset.RData")
load(file=con)
close(con)
bm = bodymap.eset
edata = exprs(bm)
pdata_bm=pData(bm)
```
Fit a linear model relating he first gene’s counts to the age of the person and the sex of the samples. What is the value and interpretation of the coefficient for age?
```r
# fit linear model
lm2 = lm(edata[1,] ~ pdata_bm$age + pdata_bm$gender)
summary(lm2)

## 
## Call:
## lm(formula = edata[1, ] ~ pdata_bm$age + pdata_bm$gender)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -734.35 -229.31   -3.26  243.02  768.09 
## 
## Coefficients:
##                  Estimate Std. Error t value Pr(>|t|)    
## (Intercept)      2331.581    438.181   5.321 0.000139 ***
## pdata_bm$age      -23.913      6.488  -3.686 0.002744 ** 
## pdata_bm$genderM -207.257    236.431  -0.877 0.396610    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 469.6 on 13 degrees of freedom
##   (3 observations deleted due to missingness)
## Multiple R-squared:  0.5147, Adjusted R-squared:   0.44 
## F-statistic: 6.894 on 2 and 13 DF,  p-value: 0.009102
```
* -23.91. This coefficient means that for each additional year of age, the count goes down by an average of 23.91 for a fixed sex.
* 2187.91. This means that for a person that is zero years old, the average count is 2187.91
* -207.26. This coefficient means that for each additional year of age, the count goes down by an average of 207.26 for a fixed sex.
* -23.91. This coefficient means that for each additional year of age, the count goes up by an average of 23.91 for a fixed sex.
### Answer
```
-23.91. This coefficient means that for each additional year of age, the count goes down by an average of 23.91 for a fixed sex.
```

## Question 5
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
Perform the log2(data + 1) transform. Then fit a regression model to each sample using population as the outcome. Do this using the 
```lm.fit``` function (hint: don't forget the intercept). What is the dimension of the residual matrix, the effects matrix and the coefficients matrix?
```r
edata = log2(edata + 1)

# fit a regression model to each sample, using population as the outcome
mod = model.matrix(~ pdata$population)
fit = lm.fit(mod, t(edata))

# dimension of the residual matrix
dim(fit$residuals)

##   -------
## [1]   129 52580
```
```r
# dimension of the effects matrix
dim(fit$effects)

##   -------
## [1]   129 52580
```
```r
# dimension of the coefficients matrix
dim(fit$coefficients)

##   -------
## [1]     2 52580
```
* Residual matrix: 52580 x 129   

  Effects matrix: 52580 x129  

  Coefficients matrix: 2 x 52580 
* Residual matrix: 52580 x 129   

  Effects matrix: 52580 x129  

  Coefficients matrix: 52580 x 2   
* Residual matrix: 52580 x 129   

  Effects matrix: 129 x 52580

  Coefficients matrix: 2 x 52580 
* Residual matrix:  129 x 52580 

  Effects matrix: 129 x 52580

  Coefficients matrix: 2 x 52580 
### Answer
```
  Residual matrix:  129 x 52580 

  Effects matrix: 129 x 52580

  Coefficients matrix: 2 x 52580 
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
Perform the log2(data + 1) transform. Then fit a regression model to each sample using population as the outcome. Do this using the 
```lm.fit``` function (hint: don't forget the intercept). What is the effects matrix?
* The model residuals for all samples for each gene, with the values for each gene stored in the columns of the matrix. 
* The model coefficients for all samples for each gene, with the values for each gene stored in the columns of the matrix. 
* The estimated fitted values for all samples for each gene, with the values for each gene stored in the rows of the matrix. 
* The estimated fitted values for all samples for each gene, with the values for each gene stored in the columns of the matrix. 
### Answer
```
* The model coefficients for all samples for each gene, with the values for each gene stored in the columns of the matrix. 
```

## Question 7
Load the Bodymap data with the following command
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bodymap_eset.RData")
load(file=con)
close(con)
bm = bodymap.eset
edata = exprs(bm)
pdata_bm=pData(bm)
```
Fit many regression models to the expression data where 
```age``` is the outcome variable using the ```lmFit``` function from the 
```limma``` package (hint: you may have to subset the expression data to the samples without missing values of age to get the model to fit). What is the coefficient for age for the 1,000th gene? Make a plot of the data and fitted values for this gene. Does the model fit well?
```r
library(devtools)
library(Biobase)
library(limma)
library(edge)

# subset the expression data to the samples without mimssing values of age
pdata_bm = na.omit(pdata_bm)
edata = edata[,rownames(pdata_bm), drop=FALSE]

# fit many regression models to the expression data where age is the outcome
mod_adj = model.matrix(~ pdata_bm$age)
fit_limma = lmFit(edata,mod_adj)

fit_limma$coefficients[1000,]

##  (Intercept) pdata_bm$age 
##   2469.87375    -27.61178
```
```r
# make a plot of the 1,000th gene and fitted values
intercept = fit_limma$coefficients[1000,][1]
slope = fit_limma$coefficients[1000,][2]
x = edata[1000,]*slope+intercept

plot(x,pdata_bm$age)
```
![alt text](https://github.com/barbaradalmaso/JHU-Genomic-Data-Science/blob/main/7.%20Statistics%20for%20Genomic%20Data%20Science/Archives/Week%202/Graph2.png)
* 2469.87. The model doesn't fit well since there appears to be a non-linear trend in the data. 
* -27.61. The model doesn't fit well since there appears to be a non-linear trend in the data.
* -27.61. The model fits well since there seems to be a flat trend in the counts. 
* -27.61. The model doesn't fit well since there are two large outlying values and the rest of the values are near zero.
### Answer
```
-27.61. The model doesn't fit well since there are two large outlying values and the rest of the values are near zero.
```

## Question 8
Load the Bodymap data with the following command
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bodymap_eset.RData")
load(file=con)
close(con)
bm = bodymap.eset
edata = exprs(bm)
pdata_bm=pData(bm)
```
Fit many regression models to the expression data where 
```age``` is the outcome variable and ```tissue.type```
is an adjustment variable using the ```lmFit``` function from the 
```limma``` package (hint: you may have to subset the expression data to the samples without missing values of age to get the model to fit). What is wrong with this model?
```r
pdata_bm$tissue.type

##  [1] adipose          adrenal          brain            breast          
##  [5] colon            heart            kidney           liver           
##  [9] lung             lymphnode        ovary            prostate        
## [13] skeletal_muscle  testes           thyroid          white_blood_cell
## 17 Levels: adipose adrenal brain breast colon heart kidney liver ... white_blood_cell
```
* Since ```tissue.type``` is a factor variable with many levels, this model has more coefficients to estimate per gene (18) than data points per gene (16).
* Normally this model wouldn't fit well since we have more coefficients (18) than data points per gene (16). But since we have so many genes to estimate with, the model fits well. 
* The model doesn't fit well since ```age``` should be treated as a factor variable.
* The model doesn't fit well because there are a large number of outliers for the white blood cell tissue. 
### Answer
```
Since ```tissue.type``` is a factor variable with many levels, this model has more coefficients to estimate per gene (18) than data points per gene (16).
```

## Question 9
Why is it difficult to distinguish the study effect from the population effect in the Montgomery Pickrell dataset from ReCount? 
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/montpick_eset.RData")
load(file=con)
close(con)
mp = montpick.eset
pdata=pData(mp)
edata=as.data.frame(exprs(mp))
fdata = fData(mp)

head(pdata)

##         sample.id num.tech.reps population      study
## NA06985   NA06985             1        CEU Montgomery
## NA06986   NA06986             1        CEU Montgomery
## NA06994   NA06994             1        CEU Montgomery
## NA07000   NA07000             1        CEU Montgomery
## NA07037   NA07037             1        CEU Montgomery
## NA07051   NA07051             1        CEU Montgomery
```
* The study effects and population effects are difficult to distinguish because the population effect is not adjusted for study. 
* The study effects and population effects are difficult to distinguish because the study effects appear in the first principal component. 
* The study effects and population effects are difficult to distinguish because the study effects are stronger. 
* The effects are difficult to distinguish because each study only measured one population. 
### Answer
```
The effects are difficult to distinguish because each study only measured one population. 
```

## Question 10
Load the Bodymap data with the following command
```r
con =url("http://bowtie-bio.sourceforge.net/recount/ExpressionSets/bodymap_eset.RData")
load(file=con)
close(con)
bm = bodymap.eset
edata = exprs(bm)
pdata_bm=pData(bm)
```
Set the seed using the command ```set.seed(33353)``` then estimate a single surrogate variable using the 
```sva function``` after log2(data + 1) transforming the expression data, removing rows with rowMeans less than 1, and treating age as the outcome (hint: you may have to subset the expression data to the samples without missing values of age to get the model to fit). What is the correlation between the estimated surrogate for batch and age? Is the surrogate more highly correlated with ```race``` or ```gender```?
```R
library(devtools)
library(Biobase)
library(sva)
library(bladderbatch)
library(snpStats)

# preprocessing the data
set.seed(33353)
pheno = na.omit(pdata_bm)
edata = edata[,rownames(pheno), drop=FALSE]
edata = log2(edata + 1)
edata = edata[rowMeans(edata) > 1,]

# fit a sva model
mod = model.matrix(~age, data=pheno)
mod0 = model.matrix(~1, data=pheno)
sva1 = sva(edata, mod,mod0, n.sv=2)

## Number of significant surrogate variables is:  2 
## Iteration (out of 5 ):1  2  3  4  5
```
```R
# correlation between surrogate for batch and age
cor(sva1$sv, pheno$age)

##            [,1]
## [1,] -0.1965417
## [2,] -0.1560322
```
```R
# correlation between surrogate for batch and race
cor(sva1$sv, as.numeric(pheno$race))

##            [,1]
## [1,] -0.2265909
## [2,] -0.1051495
```
```R
# correlation between surrogate for batch and gender
cor(sva1$sv, as.numeric(pheno$gender))

##             [,1]
## [1,] -0.35780610
## [2,]  0.04154497
```
* Correlation with age: 0.99
  
  More highly correlated with race.
* Correlation with age: 0.99

  More highly correlated with gender. 
* Correlation with age: 0.33

  More highly correlated with gender. 
* Correlation with age: 0.20

  More highly correlated with gender. 
### Answer
```
Correlation with age: 0.20

More highly correlated with gender. 
```
