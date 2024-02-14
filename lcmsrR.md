---
layout: default
title: R Tutorial
has_children: false
---
# LCM-SR R Tutorial

In the following section, we walk through each how to fit of the models presented in [Curran et al., 2014](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4067471/) in R. For each model, we include (1) annotated code, (2) annotated output, and (3) a video that walks through the code and output.  

Download Data Download R Code
1. TOC
 {:toc}

## Univariate Unconditional LCM-SRs for alcohol use & depression
### Random Intercept Only
```
alc.mod1 <- '
# ALCOHOL #
# random intercept
alc =~ 1*alc1 + 1*alc2 + 1*alc3 + 1*alc4 + 1*alc5
alc ~ 1
alc ~~ alc

# create structured residuals
alc1 ~~ 0*alc1
alc2 ~~ 0*alc2
alc3 ~~ 0*alc3
alc4 ~~ 0*alc4
alc5 ~~ 0*alc5

salc1 =~ 1*alc1
salc2 =~ 1*alc2
salc3 =~ 1*alc3
salc4 =~ 1*alc4
salc5 =~ 1*alc5

salc1 ~ 0
salc2 ~ 0
salc3 ~ 0
salc4 ~ 0
salc5 ~ 0

salc1 ~~ salc1
salc2 ~~ salc2
salc3 ~~ salc3
salc4 ~~ salc4
salc5 ~~ salc5
'

alc.fit1 <- lavaan(alc.mod1, lcmsr.sim)
summary(alc.fit1, fit.measures = T)

```
### Random Intercept and Random Slope

```
alc.mod2 <- '
# ALCOHOL #
# random intercept
alc.i =~ 1*alc1 + 1*alc2 + 1*alc3 + 1*alc4 + 1*alc5
alc.i ~ 1
alc.i ~~ alc.i

# random slope
alc.s =~ 0*alc1 + 1*alc2 + 2*alc3 + 3*alc4 + 4*alc5
alc.s ~ 1
alc.s ~~ alc.s
alc.i ~~ alc.s

# create structured residuals
alc1 ~~ 0*alc1
alc2 ~~ 0*alc2
alc3 ~~ 0*alc3
alc4 ~~ 0*alc4
alc5 ~~ 0*alc5

salc1 =~ 1*alc1
salc2 =~ 1*alc2
salc3 =~ 1*alc3
salc4 =~ 1*alc4
salc5 =~ 1*alc5

salc1 ~ 0
salc2 ~ 0
salc3 ~ 0
salc4 ~ 0
salc5 ~ 0

salc1 ~~ salc1
salc2 ~~ salc2
salc3 ~~ salc3
salc4 ~~ salc4
salc5 ~~ salc5
'

alc.fit2 <- lavaan(alc.mod2, lcmsr.sim)
summary(alc.fit2, fit.measures = T)
print(anova(alc.fit1, alc.fit2))
```
### Random Intercept, Random Slope, and Structured Residuals
```
alc.mod3 <- '
# ALCOHOL #
# random intercept
alc.i =~ 1*alc1 + 1*alc2 + 1*alc3 + 1*alc4 + 1*alc5
alc.i ~ 1
alc.i ~~ alc.i

# random slope
alc.s =~ 0*alc1 + 1*alc2 + 2*alc3 + 3*alc4 + 4*alc5
alc.s ~ 1
alc.s ~~ alc.s
alc.i ~~ alc.s

# create structured residuals
alc1 ~~ 0*alc1
alc2 ~~ 0*alc2
alc3 ~~ 0*alc3
alc4 ~~ 0*alc4
alc5 ~~ 0*alc5

salc1 =~ 1*alc1
salc2 =~ 1*alc2
salc3 =~ 1*alc3
salc4 =~ 1*alc4
salc5 =~ 1*alc5

salc1 ~ 0
salc2 ~ 0
salc3 ~ 0
salc4 ~ 0
salc5 ~ 0

salc1 ~~ salc1
salc2 ~~ salc2
salc3 ~~ salc3
salc4 ~~ salc4
salc5 ~~ salc5

# add auto-regressive paths
salc2 ~ pyy*salc1
salc3 ~ pyy*salc2
salc4 ~ pyy*salc3
salc5 ~ pyy*salc4
'

alc.fit3 <- lavaan(alc.mod3, lcmsr.sim)
summary(alc.fit3, fit.measures = T)
print(anova(alc.fit3, alc.fit2))
```

## Bivariate Unconditional LCM-SR for alcohol use & depression

## Bivariate Conditional LCM-SR for alcohol use & depression
