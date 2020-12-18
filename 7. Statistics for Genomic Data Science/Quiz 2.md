# Module 2 Quiz

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
* a. 0.89 b. 0.97 c. 0.35
* a. 0.97 b. 0.97 c. 0.97
* a. 0.97 b. 0.97 c. 0.35
* a. 0.89 b. 0.89 c. 0.35

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
* 0.87
* -0.52
* 0.33
* 0.85

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
* There are very few samples with more than 2 replicates so the estimates for those values will not be very good. 
* The difference between 2 and 5 technical replicates is not the same as the difference between 5 and 6 technical replicates. 
* The variable ```num.tech.reps``` is not a good measure of the technical variability in the data.
* There may be different numbers of counts for different numbers of technical replicates. 

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
* -23.91. This coefficient means that for each additional year of age, the count goes down by an average of 23.91 for a fixed sex.
* 2187.91. This means that for a person that is zero years old, the average count is 2187.91
* -207.26. This coefficient means that for each additional year of age, the count goes down by an average of 207.26 for a fixed sex.
* -23.91. This coefficient means that for each additional year of age, the count goes up by an average of 23.91 for a fixed sex.

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
* 2469.87. The model doesn't fit well since there appears to be a non-linear trend in the data. 
* -27.61. The model doesn't fit well since there appears to be a non-linear trend in the data.
* -27.61. The model fits well since there seems to be a flat trend in the counts. 
* -27.61. The model doesn't fit well since there are two large outlying values and the rest of the values are near zero.

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
* Since ```tissue.type``` is a factor variable with many levels, this model has more coefficients to estimate per gene (18) than data points per gene (16).
* Normally this model wouldn't fit well since we have more coefficients (18) than data points per gene (16). But since we have so many genes to estimate with, the model fits well. 
* The model doesn't fit well since ```age``` should be treated as a factor variable.
* The model doesn't fit well because there are a large number of outliers for the white blood cell tissue. 

## Question 9
Why is it difficult to distinguish the study effect from the population effect in the Montgomery Pickrell dataset from ReCount? 
* The study effects and population effects are difficult to distinguish because the population effect is not adjusted for study. 
* The study effects and population effects are difficult to distinguish because the study effects appear in the first principal component. 
* The study effects and population effects are difficult to distinguish because the study effects are stronger. 
* The effects are difficult to distinguish because each study only measured one population. 

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
```sva function``` after log2(data + 1) transforming the expression data, removing rows with rowMeans less than 1, and treating age as the outcome (hint: you may have to subset the expression data to the samples without missing values of age to get the model to fit). What is the correlation between the estimated surrogate for batch and age? Is the surrogate more highly correlated with 
```race``` or ```gender```?
* Correlation with age: 0.99
  
  More highly correlated with race.
* Correlation with age: 0.99

  More highly correlated with gender. 
* Correlation with age: 0.33

  More highly correlated with gender. 
* Correlation with age: 0.20

  More highly correlated with gender. 
