---
layout: post
title:  Just write.
date:   2016-04-28 15:31:51
category: algorithm
---

The only way to get better at something is to practice it. This morning during [N-Languages meetup](http://www.meetup.com/N-Languages-in-N-Months-NYC/) on algorithms,  I informally brainstormed with folks about how to improve skills. It became clear that consistency in working on whatever skills is going to help with achieving that goal. 

I'm committing to blogging everyday for the indefinite future, to help with developing consistency and discipline.

> "With self-discipline most anything is possible. 
> -- Theodore Roosevelt


### Today's goal 

Write a function that calculates the greatest common denominator with Haskell: 

{% highlight haskell %}
let gcd a 0 = a
    gcd a b = gcd b y
      where y = mod a b
{% endhighlight %}

What this function `gcd` does is take two numbers, the numerator and denominator. If the denominator is 0, return the numerator. Otherwise, recursively pass in denominators.

Learned over the weekend during the Haskell Workshop that when you write a let statement, the following variable definitions don't require a `let` and can just be aligned with the indentation.

![](http://www.lovethispic.com/uploaded_images/46469-Just-Did-It.jpg)

