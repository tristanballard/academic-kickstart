---
title: 'Doing Bayesian Lead-210 interpretation'
author: admin
date: '2019-05-01'
slug: []
categories: []
tags: ["R", "Tutorials"]
subtitle: 'This is the subtitle'
summary: 'This is the summary'
authors: []
lastmod: '2019-05-01T10:05:28+00:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

Read in <a href="https://cfpub.epa.gov/roe/indicator.cfm?i=33">observed</a> and Van Meter predicted MRB loading datasets and convert to consistent kg/hectare units.

``` r
head(mrb)
```

## year loadObserved loadPredVanMeter
## 1 1955     1.475376         1.192663
## 2 1956     1.036194         1.072244
## 3 1957     1.478807         1.445550
## 4 1958     1.266078         1.472036
## 5 1959     1.142558         1.260760
## 6 1960     1.108247         1.227245

## Precipitation and excess crop nitrogen
``` r
par(mfrow=c(1,2))
  plot(precip.df$year, precip.df$precip, type='l', ylab='Precipitation (mm)', xlab='Year', las=1, col='#1175BE',    lwd=1.5, main='Basin-Wide Precipitation (PRISM)', cex.main=.9)
  plot(surplus.df$year, surplus.df$crop.surplus, type='l', ylab='N Inputs (kg/ha)', xlab='Year', las=1, col='#FD8B25', lwd=1.5, main='Basin-Wide Crop N Inputs', cex.main=.9)
```

Next I read in the chloropigment data from Rabalais et al. (MPB 2004). I also verify the R2 values they provide for their model vs. the pigments. I recreate their R2 values very nearly for the 1960-1997 period (noting that the N load estimates I have are from the GBC paper, so may be slightly different than those used in the updated Science paper) but are a bit lower than reported in the 1820-1930 period.


