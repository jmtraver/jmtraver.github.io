
# Latent Curve Model with Structured Residuals
{: .no_toc}
## A tutorial by Jen Traver and Patrick Curran
{: .no_toc}


This tutorial will provide a practical introduction to the application of the latent curve model with structured residuals (LCM-SR), and is designed to accompany [Curran et al., 2014](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4067471/). Topics covered include:

1. TOC
 {:toc}


{: .note } 
The current tutorial assumes a baseline understanding of the SEM framework and latent curve models (LCMs, also referred to as latent growth models, latent growth curve models, etc.).If you are not familiar with these topics, there are several free resources where you can begin including CenterStat’s [free introduction to SEM workshop](https://centerstat.org/introduction-to-structural-equation-modeling-async/) and [YouTube playlist](https://www.youtube.com/@centerstat/playlists) dedicated to growth modeling.      

**Insert Intro Video Here**
## Background

## When to use the LCM-SR

## Data requirements and assumptions
Number of timepoints, number of observations, types of variables

## Fitting and interpreting LCM-SRs

The following section walks through the models presented in [Curran et al., 2014](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4067471/) using example data and code made available by Patrick Curran. To follow along in R or MPlus, please use the buttons below to download (1) the data and (2) code in the program of your choice.  
 
<!-- figure out how to best add code since R is all in one file and Mplus is across multiple files --> 
[Download Data](/currandemo.dat){: .btn}
[Download R Code](/LCM-SR.R){: .btn}
[Download MPlus Code](/MPlus){: .btn}

### Description of data

The data consists of artificially generated repeated measures data with a sample size of N = 250 and 5 timepionts. More details about the population generating model can be found in Curran et al., 2014. The dataset contains 13 variables:
* id: participant id (1-250)
* gen: biological sex (females = 0, males = 1)
* trt: treatment condition (control = 0, treatment = 1)
* alc1 - alc5: repeated measures of alcohol use
* dep1 - dep5: repeated measures of depression
  
### Model Building Strategy

Although there is no single model building strategy that is optimal for all situations, we will use the following framework:

1. Establish optimal fitting model within each construct separately: for each construct we will (a) determine the optimal functional form of time (linear, quadratic, etc.), (b) test the autoregressions among residuals, and (c) test if the autoregressions are approximately equivalent across time.
2. Estimate a model for both constructs simultaneously: conduct tests of (a) across-construct relationships at the level of the latent variable, (b) across-construct relationships at the level of the time-structured residuals, and (c) equality constraints on the cross-lagged regressions.
3. Expand multivariate model to include predictors of interest

At each step, we will conduct likelihood ratio tests (LRTs) to evaluate the change in model fit. 



[R Tutorial](https://jmtraver.github.io/lcmsrR.html) {: .btn .btn-purple}
[MPlus Tutorial](https://jmtraver.github.io/lcmsrMPlus.html) {: .btn .btn-green}


---
