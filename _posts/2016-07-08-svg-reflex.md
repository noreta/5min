---
layout: post
title: svg with reflex
date: 2016-07-08 19:31:17
tags: haskell, reflex
category: haskell
---

A friend needed help figuring out why code didn't compile when [creating an SVG element with reflexfrp][1].

I explained how the element creation requires a specific format.

{% highlight haskell %}
import Reflex.Dom
import qualified Data.Map as Map

main = mainWidget $ myDiv

myDiv = el "svg" $ do
  elAttr "circle"  (Map.fromList [ ("cx" , "50") , ("cy", "50"), ("r" , "40"), ("stroke" , "green"), ("fill",  "yellow" )]) $ return ()
{% endhighlight %}

It is basically saying create a svg tag, with the specified attributes. `elAttr` has a type signature of `elAttr :: String -> Map String String  -> m a -> m a`, which if you match would mean that there are two inputs. 

The first input: *`String`* is `"circle"` 

and the second input: *`Map String String`* is everything inside the parentheses `Map.fromList [ ("cx" , "50") , ("cy", "50"), ("r" , "40"), ("stroke" , "green"), ("fill",  "yellow" )]`

The second input should be wrapped with parentheses `()` so that the type signatures match. I'm not sure exactly why the syntax works like this however that is what the compiler needs to see to understand.

Once compiled the output would look like this: 

{% highlight html %}
<html>
  <head>
    <script language="javascript" src="rts.js"></script>
    <script language="javascript" src="lib.js"></script>
    <script language="javascript" src="out.js"></script>
  </head>
  <body>
    <svg>
     <circle cx="50" cy="50" fill="yellow" r="40" stroke="green"></circle>
    </svg>
  </body>
</html>
{% endhighlight %}

Final note, to have SVGs show up in the browser, you need to define the xmlns attribute:

{% highlight html %}
<svg xmlns="http://www.w3.org/2000/svg">
  <circle cx="50px" cy="50" fill="yellow" r="40" stroke="green"></circle>
</svg>
{% endhighlight %}

The end result is a yellow circle:

<svg xmlns="http://www.w3.org/2000/svg">
  <circle cx="50px" cy="50" fill="yellow" r="40" stroke="green"></circle>
</svg>

[1]: http://stackoverflow.com/questions/38268962/a-single-svg-element-with-reflex-frp/38270441#38270441
