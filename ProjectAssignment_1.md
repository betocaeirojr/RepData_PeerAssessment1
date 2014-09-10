# Reproducible Research: Peer Assessment 1
Alberto A. Caeiro Jr  
This project is part of the Johns Hopkins University, offered by Coursera.


### Setting Working Folder

```r
setwd('/Users/acaeiro/Developer/Data Science Specialization/RepData_PeerAssessment1')
```

### Loading and preprocessing the data
The dataset is zipped, so we have to unzip it and then load into R.


```r
zipFile <- "./activity.zip"
fileList <- unzip(zipFile)
activity <- read.csv(fileList[1], sep=",", header=TRUE)
```

The date column needs to be reformatted to DATE format.

```r
activity$date <- as.Date(activity$date, format="%Y-%m-%d")
str(activity)
```

```
## 'data.frame':	17568 obs. of  3 variables:
##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date    : Date, format: "2012-10-01" "2012-10-01" ...
##  $ interval: int  0 5 10 15 20 25 30 35 40 45 ...
```

## What is mean total number of steps taken per day?

1. Total numbers of steps taken Each Day (Hist)

```r
byValue=list(Date = activity$date)
aggregatedActivity <- aggregate(activity$steps, by=byValue, FUN=sum, na.rm=TRUE)
names(aggregatedActivity) <- c("Date", "Sum.Of.Steps")
with(aggregatedActivity, hist(Sum.Of.Steps, col=Date, xlab="Total Steps per Day"))
```

![plot of chunk unnamed-chunk-4](./ProjectAssignment_1_files/figure-html/unnamed-chunk-4.png) 

2. Mean total number of steps

```r
byValue=list(Date = activity$date)
aggregatedActivity <- aggregate(activity$steps, by=byValue, FUN=mean, na.rm=TRUE)
names(aggregatedActivity) <- c("Date", "Average.Of.Steps")
with(aggregatedActivity, plot(Date, Average.Of.Steps, type="l", ylab="Mean - Daily Total Steps"))
```

![plot of chunk unnamed-chunk-5](./ProjectAssignment_1_files/figure-html/unnamed-chunk-5.png) 

3. Median

```r
byValue=list(Date = activity$date)
aggregatedActivity <- aggregate(activity$steps, by=byValue, FUN=median, na.rm=TRUE)
names(aggregatedActivity) <- c("Date", "Median.Of.Steps")
with(aggregatedActivity, plot(Date, Median.Of.Steps, type="l", ylab="Median - Daily Total Steps"))
```

![plot of chunk unnamed-chunk-6](./ProjectAssignment_1_files/figure-html/unnamed-chunk-6.png) 

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
