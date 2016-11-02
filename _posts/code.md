---
layout: post
title: Energy dataset
author: Andy South
published: true
status: publish
draft: false
tags: R Jekyll RStudio
---
 
 
***
 
#### Abstract: 
This study looked into assessing the heating load and cooling load requirements of buildings (that is, energy efficiency) as a function of building parameters.
 
 
***
 
### Data set information:
 
We perform energy analysis using 12 different building shapes simulated in Ecotect. The buildings differ with respect to the glazing area, the glazing area distribution, and the orientation, amongst other parameters. We simulate various settings as functions of the afore-mentioned characteristics to obtain 768 building shapes.
 
 
Our aim is to use a model to predict the Heating Load and the cooling Load using the eight features below:
 
Specifically: 
 
* Relative Compactness 
* Surface Area 
* Wall Area 
* Roof Area 
* Overall Height 
* Orientation 
* Glazing Area 
* Glazing Area Distribution 
* Heating Load 
* Cooling Load
 

{% highlight text %}
## Error: 'ENB2012_data.xlsx' does not exist in current working directory ('C:/Users/daniel/Documents/GitHub/abbandaniel.github.io').
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): object 'building' not found
{% endhighlight %}
 
 

{% highlight text %}
## Error in names(building) <- c("compactness", "surfaceArea", "wallArea", : object 'building' not found
{% endhighlight %}
 
***
 
The data contains 8 predictors and 2 outcomes we are modeling

{% highlight text %}
## Error in str(building): object 'building' not found
{% endhighlight %}
 
***
 
We observe the summary of the data below

{% highlight r %}
summary(building)
{% endhighlight %}



{% highlight text %}
## Error in summary(building): object 'building' not found
{% endhighlight %}
 
***
 
Remove the missing values:

{% highlight r %}
building <- building %>%
        filter(!is.na(compactness))
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): object 'building' not found
{% endhighlight %}
 
 
 
 Glazing area is a part of a wall or window, made of glass
 Glazing can be mounted on the surface of a window sash or door stile, usually made of wood, aluminium or PVC.
 Glazing is commonly used in low temperature solar thermal collectors because it helps retain the collected heat.
 
***
 

{% highlight r %}
building2 <- select(building, -HeatingLoad)
{% endhighlight %}



{% highlight text %}
## Error in select_(.data, .dots = lazyeval::lazy_dots(...)): object 'building' not found
{% endhighlight %}



{% highlight r %}
# romove correlation:
correlation <- cor(building2)
{% endhighlight %}



{% highlight text %}
## Error in is.data.frame(x): object 'building2' not found
{% endhighlight %}



{% highlight r %}
tooHigh <- findCorrelation(correlation, cutoff = .75)
{% endhighlight %}



{% highlight text %}
## Error in is.data.frame(x): object 'correlation' not found
{% endhighlight %}



{% highlight r %}
filtBuilding <- building2[, -tooHigh]
{% endhighlight %}



{% highlight text %}
## Error in eval(expr, envir, enclos): object 'building2' not found
{% endhighlight %}



{% highlight r %}
# remove near-zero variance
nzv <- nearZeroVar(filtBuilding, saveMetrics = TRUE)
{% endhighlight %}



{% highlight text %}
## Error in nzv(x, freqCut = freqCut, uniqueCut = uniqueCut, saveMetrics = saveMetrics, : object 'filtBuilding' not found
{% endhighlight %}



{% highlight r %}
# Fit the linear model:
lmFit <- lm(CoolingLoad ~ ., data = filtBuilding)
{% endhighlight %}



{% highlight text %}
## Error in is.data.frame(data): object 'filtBuilding' not found
{% endhighlight %}



{% highlight r %}
summary(lmFit)
{% endhighlight %}



{% highlight text %}
## Error in summary(lmFit): object 'lmFit' not found
{% endhighlight %}



{% highlight r %}
ggcorr(filtBuilding)
{% endhighlight %}



{% highlight text %}
## Error in ggcorr(filtBuilding): object 'filtBuilding' not found
{% endhighlight %}



{% highlight r %}
hisFuc <- function(x){
        ggplot(building2, aes(x = x)) +
                geom_histogram(bins = 50)
        ggplotly()
}
 
hisFuc(building2$compactness)
{% endhighlight %}



{% highlight text %}
## Error in ggplot(building2, aes(x = x)): object 'building2' not found
{% endhighlight %}



{% highlight r %}
hisFuc(building2$surfaceArea)
{% endhighlight %}



{% highlight text %}
## Error in ggplot(building2, aes(x = x)): object 'building2' not found
{% endhighlight %}



{% highlight r %}
hisFuc(building2$wallArea)
{% endhighlight %}



{% highlight text %}
## Error in ggplot(building2, aes(x = x)): object 'building2' not found
{% endhighlight %}



{% highlight r %}
hisFuc(building2$OverallHeight)
{% endhighlight %}



{% highlight text %}
## Error in ggplot(building2, aes(x = x)): object 'building2' not found
{% endhighlight %}



{% highlight r %}
hisFuc(building2$Orientation)
{% endhighlight %}



{% highlight text %}
## Error in ggplot(building2, aes(x = x)): object 'building2' not found
{% endhighlight %}



{% highlight r %}
hisFuc(building2$GlazingArea)
{% endhighlight %}



{% highlight text %}
## Error in ggplot(building2, aes(x = x)): object 'building2' not found
{% endhighlight %}



{% highlight r %}
hisFuc(building2$CoolingLoad)
{% endhighlight %}



{% highlight text %}
## Error in ggplot(building2, aes(x = x)): object 'building2' not found
{% endhighlight %}



{% highlight r %}
ggplot(building2, aes(x = Orientation)) +
        geom_histogram(bins = 50)
{% endhighlight %}



{% highlight text %}
## Error in ggplot(building2, aes(x = Orientation)): object 'building2' not found
{% endhighlight %}
