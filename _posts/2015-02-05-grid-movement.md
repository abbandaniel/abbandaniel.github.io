---
layout: post
title: my trial post
author: daniel abban
published: true
status: publish
draft: false
tags: R 
---
 
This is yet another document of mine, just to try out R markdown.  End a line with two space to start a new paragraph. make a text italics like this *italics* or _italicsagain_. This makes a text **bold** 
 
This is how to insert a link in your R markdown documents. [here](www.datalampconsult.com). 
 
> This is how to insert a block quote
 
Now i want to make an unordered list.
 
 * First list
 * Second list
     + sub1
     + sub2
 
 
  
What if i want to make a ordered list.
 
1. Number one
2. Number two
      + sub number1
      + sub number2
      
***
 
When you surround your codes with backticks and r. R replaces inline code with its result. Two plus two equals 4.
 
 
 
now the beauty of R markdown. lets go ahead and add some code chunks, observe carefully how this is done. 

{% highlight r %}
head(iris)
{% endhighlight %}



{% highlight text %}
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 1          5.1         3.5          1.4         0.2  setosa
## 2          4.9         3.0          1.4         0.2  setosa
## 3          4.7         3.2          1.3         0.2  setosa
## 4          4.6         3.1          1.5         0.2  setosa
## 5          5.0         3.6          1.4         0.2  setosa
## 6          5.4         3.9          1.7         0.4  setosa
{% endhighlight %}
