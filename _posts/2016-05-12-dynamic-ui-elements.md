---
layout: post
title: designing for frp
date: 2016-05-12 14:53:00
tags: haskell
category: haskell
---

I've been learning ReflexFRP by building a single page app, a graphical user interface (GUI) for calculating image aspect ratios. I wanted the ability to preview images with new image aspect ratios, and maybe someday also preview cropped images). The preview element changes shape depending on the numbers specified in the form inputs, as you can see in the preview below. 

My approach for building this app has been from a designer perspective as you would be able to see from my commit log that I included the CSS and semantic DOM elements before figuring out how the dynamic behavior works :smile_cat:

Here is a preview of the UI in action.

![](/assets/img/elDynAttr.gif)

I mentioned having a designer perspective because the Reflex-FRP and Reflex-Dom has a different way of thinking. When I asked for help with coding my general format follows: (1) explain objective with GUI specs, (2) list docs referenced, (3) brief description of what I understand and attempted to do, and (4) hypothesis on where my knowledge gap lies and/or the confusion on how to put pieces together. Well, the answer in this particular case was that **UX Design has a different way of modeling the GUI than an FRP system**. I write this but don't know how to explain the particulars in technical terms, hopefully the example below illustrates my point.

I wanted to know how to make the placeholder image change its shape depending on numbers inputted. I figured out it was a dynamic, some sort of `elDynAttr` because the `x` and `y` values are not constants, but didn't know how to pass in the number values. It's important to understand the types because coding in Haskell when you're doing it right is like connecting pipes. It turns out `elDynAttr'` is a better choice as it returns a dynamic element type.

From the Reflex-Dom [quickref](https://github.com/reflex-frp/reflex-dom/blob/develop/Quickref.md):

{% highlight haskell %}
elDynAttr  :: String -> Dynamic (Map String String) -> m a -> m a
elDynAttr' :: String -> Dynamic (Map String String) -> m a -> m (El, a)
{% endhighlight %}

#### Working with Reflex-Dom


FRP views the breakdown of interaction flows as a system of *events* and *behaviors*. In Reflex-Dom you have these and also the dynamic type. I mistakenly thought user events like the ones you might see in Javascript (keypress, mouseclick, etc), but it's not just that, there's also somewhat of a [Rube Goldberg Machine][4] setup to think about.

For example, with my ux design hat on I saw 4 text boxes for the user, each with a label on the side and then a placeholder image area. A user will most likely start from the left pair to find out what the image ratio is and then using that ratio figure out the correct measurements for the resulting image. As I'm learning Reflex-Dom, I realize it's easier to code the left and right sides separately for now, it's more complicated to connect the interactions of a grouping of GUI elements. As you add more GUI elements, you have more data to think about passing values around. Working with user-defined values requires a lot more code!

> When writing Reflex-Dom apps, bear in mind the order of elements specified as it will affect the order in which the events and behaviors flow through the FRP mini-verse.

#### How the code works

In the most recent commit to my Getting Started With Haskell repo [#f1336ec](https://github.com/katychuang/getting-started-with-haskell/blob/f1336ec34618446bea5be65e5c31b7d933d10332/tutorials/img-ratio/reflex_ui.hs), the code specifies the dynamic behavior of the image preview with the [elDynAttr'](https://hackage.haskell.org/package/reflex-dom-0.3/docs/Reflex-Dom-Widget-Basic.html#v:elDynAttr-39-) function. The preview placeholder responds to the events created when the textboxes are updated.

In the 2nd line you'll see `rec` which is some sort of virtual container telling the compiler to let the values be used in any order in the subset. That's how you get around the rule in blockquotes above about knowing the order in which elements are created.

{% highlight haskell %}
elClass "div" "left" $ do
  rec
    attrs <- combineDyn (\x y -> imgAttrs x y) x1 y1
    elDynAttr' "img" (attrs) $ return ()

    x1 <- box "x1  =" "1024" never
    y1 <- box "y1  =" "768" never

  text "ratio = "
  r <- combineDyn (\x y -> calcAspectRatio x y) x1 y1
  result <- mapDyn show r
  dynText result
{% endhighlight %}

In case you're wondering about `imgAttrs` and `calcAspectRatio`, I defined those functions and you can see what they're about below:

{% highlight haskell %}
calcAspectRatio :: Maybe Double -> Maybe Double -> Double
calcAspectRatio x y = case (x, y) of
  (Just x', Just y') -> x' / y'
  _ -> 4.3


imgAttrs :: Maybe Double -> Maybe Double -> Map String String
imgAttrs x y = case (x, y) of
  (Just x', Just y') -> "src" =: ("http://placehold.it/" ++ (show x') ++"x"++ (show y')) <> style <> static
  _ -> Map.empty
  where
    static = "width" =: "400"
    style = "style" =: "border: 1px solid red; margin-bottom: 25px;"

{% endhighlight %}


Here's a use case showing how the calculated image aspect ratio based on the `calcAspectRatio` function above. We don't know if the user will input expected real number values, which is why I've the case statements for when there are legitimate values and when it's null. The `imgAttrs` function takes two numbers and returns the image place holder.

![](https://lh3.googleusercontent.com/1PY30opzyNb3CLyMw9khLvcIafDJrRPA23LVXMpzyEt68JxihpIcp3sz8MoIvQy7wN9YB8XnSHlUpv0lKTfkLdh4nZw14a5rc0tjO1yajYkFTePsVwwIIMSVzdiZuC4CgvfsN0EVpa_yGQ3SLQ-QNXIVt_uZZx3VVnODv8BuqiZZM589gqOnPcX45WhUCdP8mSnpZVWsU4GxKI4ie6-NMzqbdSSuNax-NJUPZH92D0ftsnzWcJxSSfrdu9NWoxYdkPPXjhusVulWwzvKnqIAblJobHVGIv4W8E7h3r6HRnKgpTycHlEM5V6UPowYU69BETmmfS6T2d2kzPwdzE1eHNSFd8A8tl2PIOnNjq3f2Zr3OoMYYXWC_SrSd6f17_o4P5j6NFV4RA4UIEtTLIUqXM-S1I8RS6MRLGrC9KAaQF5w-L6LCWo9yDuJCVjW312hOdDAEKFdMPPPo03uJbQC-iO3mjppM-qjuZCPXB0cATPk_FFf-AVm6UpoyWYWyGlburzFYnM62TRP_VAC4A-qRiVmh6fZw405RlxccOKFRpP3q_zGVTehaOJTDTAntijAC_Hw1xCA_7nq0QJISmXE99eDKWIKKKRp=w553-h350-no)


[1]: http://www.silisoftware.com/tools/screen.php
[2]: https://www.digitalrebellion.com/webapps/aspectcalc
[3]: http://andrew.hedges.name/experiments/aspect_ratio/
[4]: https://en.wikipedia.org/wiki/Rube_Goldberg_machine
