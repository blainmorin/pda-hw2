# pda-hw2
data analysis, simulation


This assignment has two parts. In the first, you will analyze some data and write up a report. This report should look like a publication (i.e. text and figures/tables should be interspersed with explanations of the methods used and interpretations of the results. Code used to carry out the calculations should appear as an Appendix at the end of the report. The second part involves a simulation exercise.

 

The PhD/extra credit problems are required for Biostatistics PhD students but are extra credit for everyone else. Future homeworks will have problems of this type.

Part A

Use the data in the baseseg.csv file on kidney disease to construct a good fitting model for GFR as a function of the following potential predictors measured at baseline 

1) Serum Creatinine (bascre); 2) Systolic blood pressure (sbase); 3) Diastolic blood pressure (dbase); 4)Urine protein (baseu); 5) Age; 6) Gender (Sex = 1 if male; = 0 if female); 7) African-American (black) 

Consider potential transformations of the outcome and variables as well as interaction terms. 

Examine the fit of your model by regression diagnostics by checking model assumptions such as constancy of variance, linearity, normality and characteristics such as outliers, influence, etc). 

Describe your findings in clearly written text, tables and figures. Discuss which factors are predictive and how. Show some predictive plots showing outcomes as a function of the predictors (see Papers 13 and 14 for examples). 

 

Part B

This exercise will allow you to explore the phenomenon of overfitting in linear regression through simulation. All problems marked extra credit are optional except for the PhD students in biostatistics.

 

1. First you will explore type 1 and type 2 errors with a simple regression.

 

Simulate a random vector y of length 100 in which each element follows a normal distribution with mean 10 and variance 4. Then simulate a random vector x of length 100 with mean 3 and variance 1.
Regress y on x and save the p-value for the slope (HINT: use the summary.lm function or summary(lmobject) and use the coef element of the summary object if using R)
What do you think this p-value should be?
Now replicate this procedure 1000 times to develop a simulation.
Calculate the proportion of times the p-value is less than 0.05. How does this match with your intuition? [HINT: Should the slope be related to the outcome? What type of error are you simulating?]
Now simulate y and x together so that the conditional mean of y given x is 10+x and the conditional variance is 1. Repeat b-e above for this distribution. How does your answer differ from the first simulation? What are you simulating now? [HINT: Consider if the slope is actually related to the outcome]
 

 

2. Now we will investigate overfitting which occurs when you are making too complex a model. First we will simulate some data in which y and multiple x's are unrelated

 

Extend the function you have written to carry out exercise 1 so that you now generate the same y vector as in 1a (i.e. 100 draws from N(10,4)) but you now generate 100 draws from an 3-variate multivariate normal X matrix with means 1, 2, 3 and covariance matrix equal to the identity matrix of rank 3 (i.e., each X variable has variance 1 and they are uncorrelated). [HiNT: use the mvrnorm function in the MASS library to generate multivariate normal draws].
Regress y on the X matrix and save the p-values from this regression. In R if you specify X as a matrix in the call to the lm() function, it will automatically use the formula y~x[,1]+x[,2]+… i.e. it will use the columns of the matrix as the predictors.
Determine how many of the p-values for each variable are significant at the 0.05 level.
Compute the minimum p-value for each regression and calculate how many times the minimum p-value is less than 0.05. Why is this answer different from those in question c?
Now repeat this exercise changing the number of predictors P so that you do it for P = 3, 5, 10, 20, 50, 90. Compute the minimum p-value in each simulated regression and plot the number of times you find at least one significant variable for each P. What pattern do you see? How do you explain this?
Set P equal to every number from 1 to 99 (i.e. you try models with all possible number of predictors) and run more simulations to reduce simulation error.
 

3. (PhD students/Extra credit for others) Repeat exercise 2 but now using correlated predictors. To do this you need to change the covariance matrix for X to allow for correlation. We will assume the correlation between each pair of X variables is 0.5. This implies what covariance assuming the variances are all 1? Use this covariance to set up a correlated X matrix and then repeat the rest of the steps. Explain your findings.

 

4. (PhD students/Extra credit for others) Assume that y = f(X) + e is the true model. You have estimated f by a function g(X). Show that the square of the expected error E(Y-g(X)] equals the sum of the variance of g(X), the square of the bias of g(X), and the variance of the irreducible error from e.

 

5. (PhD students/Extra credit for others) Given inputs x and outputs y and a model f(x) fit by least squares. Show that if there are observations with identical values of x, then the fit can be obtained from a reduced weighted least squares problem.