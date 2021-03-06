---
title       : Tracker using dummy firm data
subtitle    : Shiny App for Coursera Data Products Class
author      : TSWenzel
job         : Analyst
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Overview
- This shiny App allows you to plot 2 variables for a particular firm.
- You can see the output both plotted over time, as well as detailed in the table below. 
- The underlying data will be sorted ascendingly for y1 and the table is dynamic in the sense that you can click on a column which will sort the selected column for you.

--- .class #id publish(user = "USER", repo = "REPO")

## How to use this tracker

- Both the graph and the data table can be displayed for a particular firm or for the entire set of firms. 
- Moreover, you can display this in your desired frequency using the drop down menu options. 

  1. Last month will display the data in daily frequency
  2. Last Quarter will display the data in weekly frequency
  3. "Last year" and  "All" will display the data in monthly frequency


--- .class #id 

## Example

For example, the UI selection "All" firms for the entire date range, would create the graph using the following R code




```r
tabledta<-summaryBy(y1+y2~MONTHDATE+x1,data=testData1,FUN=sum,keep.names=TRUE)
data.melt <- melt(tabledta,id.vars=c('MONTHDATE','x1'),all=TRUE)
p<-ggplot(data.melt,aes(x=MONTHDATE, y=value,group=variable,colour=variable))+geom_line()+facet_wrap(~x1,scales='free_y',ncol=1)+ylab("value of y1 and y2")+ theme(axis.text.x = element_text(angle = -90, hjust = 1))
```


--- .class #id 

## Graph

```r
p
```

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2.png) 


--- .class #id 


## Reference


Shiny App on Server: 
- http://tswenzel.shinyapps.io/Coursera/

Server.R and Ui.file as well as Slidify presentation
- https://github.com/tswenzel/DataProductsAssignment

