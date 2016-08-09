---
layout: post
title: reflex + svg examples
date: 2016-08-09 14:31:17
tags: svg, haskell
category: haskell
---

[last month](/5min/2016/07/08/svg-reflex/) I helped a friend work through [creating an svg element with reflexfrp][0]. it would not show up in the browser so have been trying to figure out how to get this working.

First tried compiling `ghcjs svg.hs` (below) with the following contents.

{% highlight sh %}
$ ghcjs svg.hs
{% endhighlight %}

{% highlight haskell %}
-- svg.hs
import reflex.dom
import qualified data.map as map

main = mainwidget $ mydiv

mydiv = el "svg" $ do
  elattr "circle"  (map.fromlist [ ("cx" , "50") , ("cy", "50"), ("r" , "40"), ("stroke" , "green"), ("fill",  "yellow" )]) $ return ()
{% endhighlight %}


it compiles into a working webpage, however nothing shows up in the browser! whaaaaat??? time to delve into the svg docs from w3 to see what might be required when [defining an svg tag properly][1]

> an svg document fragment can range from an empty fragment (i.e., no content inside of the ‘svg’ element), to a very simple svg document fragment containing a single svg graphics element such as a ‘rect’, to a complex, deeply nested collection of container elements and graphics elements. *- w3.org*

As I read further, they tell me my svg elements should look like this: 

{% highlight html %}
<svg xmlns="http://www.w3.org/2000/svg" …>
  <rect …/>
</svg>
{% endhighlight %}

edited `svg.hs` and tried again, using `elattr` instead of `el` to add attributes to the svg element but guess what, this also didn't show anything in the browser. :frowning:

{% highlight haskell %}
-- don't do this, it won't work
elattr "svg" 
    ("xmlns" =: ns 
      <> "width" =: "200.0" 
      <> "height" =: "200.0"
      <> "viewbox" =: "0 0 50 20"
      <> "xmlns:xlink" =: "http://www.w3.org/1999/xlink"
      <> "version" =: "1.0" 
      <> "xmlns:svg" =: "http://www.w3.org/2000/svg"
    )
{% endhighlight %}

Next, looked for working examples to see how others tackle this problem. In the course of this I found two places that posted examples.

### Diagrams-Reflex

There are working examples of using the graphics [diagrams][9] library to render svg elements with reflex in the [diagrams-reflex][2] repo. 

At this time there are three known examples with this repo: (1) [Click counting][3], [source][4]; (2) [Mouse position][5], [source][6]; and (3) Colors, [source][8]

No documentation found.

### Rotating Cube

On another site, an [example of a rotating cube](http://rosettacode.org/wiki/Draw_a_rotating_cube). Note, to work with the try-reflex default install you'd need to add the matrix library to list of packages.

This was the one that made me see that both the `"svg"` and `"polygon"` tags call this one function that uses `elDynAttrNS'`:

{% highlight haskell %}
elDynAttrSVG a2 a3 a4 = do 
    elDynAttrNS' (Just "http://www.w3.org/2000/svg") a2 a3 a4
    return ()
{% endhighlight %}

Bingo.

---

## Summary

What I learned - when working with the xml namespace, there's a specific function available in reflex-dom and this can also be used to produce dynamic svg elements. Is the dynamic version better than a static `elAttr`? No clue, but using `elDynAttrNS'` works and I'll be scaling towards creating dynamic graphics in the browser I'll probably stick to picking that option.

**What is elDynAttrNS'?**

From the Hackage [docs](https://hackage.haskell.org/package/reflex-dom-0.3/docs/Reflex-Dom-Widget-Basic.html) we can read the type signature.

`elDynAttrNS' :: forall t m a. MonadWidget t m => Maybe String -> String -> Dynamic t (Map String String) -> m a -> m (El t, a)` 

What this means: four inputs, the first is the xml namespace declaration, the 2nd the svg element, the third includes further attributes, and the last is a monad. This returns a monad, so you have to bind it to something~

{% highlight haskell %}
example <- elDynAttrNS' (Just "http://www.w3.org/2000/svg") "svg" attributes mAttr

-- don't do this
elAttr "svg" ("xmlns" =: ns <> "width" =: "200.0" <> "height" =: "200.0"
             <> "viewBox" =: "0 0 50 20"
             <> "xmlns:xlink" =: "http://www.w3.org/1999/xlink"
             <> "version" =: "1.0" <> "xmlns:svg" =: "http://www.w3.org/2000/svg"
             ) $ do


-- do this instead
 s <- elDynAttrNS' ns "svg" attrs (elDynAttrNS' ns "circle" cAttrs $ return ())
{% endhighlight %}


Ahh success. Feels good to have figured out a working solution. I'll update the sample `svg.hs` file with the working code :smile:



[0]: http://stackoverflow.com/questions/38268962/a-single-svg-element-with-reflex-frp/38270441#38270441

--- 
Links

[Keywords](https://wiki.haskell.org/Keywords)


[1]: https://www.w3.org/TR/SVG/struct.html#NewDocumentOverview
[2]: https://github.com/diagrams/diagrams-reflex
[3]: http://bergey.github.io/gooey/diagrams-reflex-counting/
[4]: https://github.com/diagrams/diagrams-reflex/blob/master/example/src/Counting.hs
[5]: http://bergey.github.io/gooey/diagrams-reflex-follow/
[6]: https://github.com/diagrams/diagrams-reflex/blob/master/example/src/Follow.hs
[8]: https://github.com/diagrams/diagrams-reflex/blob/master/example/src/Colors.hs
[9]: https://github.com/diagrams/diagrams
