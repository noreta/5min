---
layout: post
title: syntactic sugar
date: 2016-09-21 18:04:54
tags: 
category: haskell
---

Had a chance to pair program in Haskell today. Someone with a couple years more experience, so not too far advanced to be impatient about when I had questions.

Learned that there's several ways to express instructions in Haskell. Each of these lines do the same thing but are varying levels of conciseness. It's cool seeing them all next to each other.

{% highlight haskell %}
-- anonymous function
\file -> either error id (eitherDecode file)

-- $ to reduce parentheses
\file -> either error id $ eitherDecode file

-- composition
(either error id . eitherDecode file)
{% endhighlight %}

Here's another example for binding

{% highlight haskell %}
-- do block
server = do
  events <- liftIO loadConfig
  return events

-- anonymous function
server = liftIO loadConfig >>= \event -> return event

-- monad bind
server = liftIO loadConfig >>= return
{% endhighlight %}

