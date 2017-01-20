---
title: "PA1_template.Rmd"
author: "Monica"
date: "28 de diciembre de 2016"
output:
  html_document: default
  pdf_document: default
---

##Reproducible Research: Peer Assessment 1

```{r, cache=TRUE}
source("R_week2.R")
```

#1. Loading and preprocessing the data
 
```{r, echo=TRUE} 
 activity<- read.csv("activity.csv", sep = ";", header=TRUE)
```

-checking the dataset variables

```{r, echo=TRUE} 
names(activity)

```
-checking the type data

```{r, echo=TRUE}
 str(activity)
```

-checking the dataset head and tail
```{r, echo=TRUE}
head(activity)
tail(activity)
```
-getting a summary of the dataset.
```{r, echo=TRUE}
summary(activity)
```
#Process/transform the data (if necessary) into a format suitable for your analysis

```{r, echo=TRUE}
activity <- transform(activity, date = as.Date(date, "%Y-%m-%d"))


```

#2. What is mean total number of steps taken per day?

```{r, echo=TRUE}
data_dailysummary <- aggregate(steps ~ date, data = activity, sum, na.rm = TRUE)
```

-Plotting a histogram to visualize the distribution of the total number of steps per day

```{r, echo=TRUE}
hist(data_dailysummary$steps, 
     main = "Total steps per day", 
     xlab = "Steps per Day", 
     ylab="Freq", 
     col = "white")
```


-Calculate and report the mean and median of the total number of steps taken per day
```{r, echo =TRUE}
mean_steps=mean(data_dailysummary$steps)
median_steps=median(data_dailysummary$steps)
```
The mean is $`r mean_steps`$
The median is $`r median_steps`$

```