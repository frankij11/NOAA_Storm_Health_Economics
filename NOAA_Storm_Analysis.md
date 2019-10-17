---
title: 'NOAA Storm Database: Health and Economic Impacts'
author: "Kevin Joy"
date: "10/15/2019"
output: 
  html_document:
    keep_md: true
---



## Executive Summary

This project involves exploring the U.S. National Oceanic and Atmospheric Administration's (NOAA) storm database. This database tracks characteristics of major storms and weather events in the United States, including when and where they occur, as well as estimates of any fatalities, injuries, and property damage.  

The data analysis addresses the following questions:

1. Across the United States, which types of events (as indicated in the \color{red}{\verb|EVTYPE|}EVTYPE variable) are most harmful with respect to population health?

2. Across the United States, which types of events have the greatest economic consequences?


## Data Analysis:

### 1. Data Processing
- Load necessary packages

```r
library(tidyverse)
```

```
## ── Attaching packages ───────────────────────────────────────────────── tidyverse 1.2.1 ──
```

```
## ✔ ggplot2 3.2.1     ✔ purrr   0.3.2
## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
## ✔ tidyr   0.8.3     ✔ stringr 1.4.0
## ✔ readr   1.3.1     ✔ forcats 0.4.0
```

```
## ── Conflicts ──────────────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```

```r
library(lubridate)
```

```
## 
## Attaching package: 'lubridate'
```

```
## The following object is masked from 'package:base':
## 
##     date
```

- Download data csv file does not exist unzip activity.zip

```r
data_url <- "https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2FStormData.csv.bz2"
dataName <- "data/storm.csv.bz2"
if(!dir.exists("data")){dir.create("data")}


if(!file.exists(dataName)){
    download.file(data_url, dataName)
    #no need to unzip
  }
storm <- read.csv(dataName, nrows = 100000)
```

- Dates are stored as factor. Let's convert the factor dates to regular dates using the lubridate package


```r
date_fields <- c("BGN_DATE", "END_DATE")
storm[, date_fields] <- mdy_hms(storm[,date_fields])
```

```
## Warning in regexpr(reg, x, ignore.case = TRUE, perl = TRUE): back-tracking
## limit reached in PCRE for element 2

## Warning in regexpr(reg, x, ignore.case = TRUE, perl = TRUE): back-tracking
## limit reached in PCRE for element 2

## Warning in regexpr(reg, x, ignore.case = TRUE, perl = TRUE): back-tracking
## limit reached in PCRE for element 2

## Warning in regexpr(reg, x, ignore.case = TRUE, perl = TRUE): back-tracking
## limit reached in PCRE for element 2

## Warning in regexpr(reg, x, ignore.case = TRUE, perl = TRUE): back-tracking
## limit reached in PCRE for element 2

## Warning in regexpr(reg, x, ignore.case = TRUE, perl = TRUE): back-tracking
## limit reached in PCRE for element 2

## Warning in regexpr(reg, x, ignore.case = TRUE, perl = TRUE): back-tracking
## limit reached in PCRE for element 2

## Warning in regexpr(reg, x, ignore.case = TRUE, perl = TRUE): back-tracking
## limit reached in PCRE for element 2
```

```
## Warning: All formats failed to parse. No formats found.
```

```r
#filter to only show values greater than 2000
storm <- filter(storm, BGN_DATE >= "2000-01-01")
```


### 2. Results

#### + Types of events that are most harmful to population health:


#### + Types of events that have the greatest economic consequences:
    


