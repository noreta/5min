---
layout: post
title:  hakyll template
date:   2016-05-02 12:31:51
category: haskell
---

While working on an algorithm problem today, I received [an issue](https://github.com/katychuang/hakyll-cssgarden/issues/4) on an open source repo. I was asked about a build error for one of the templates in [Hakyll CSS Garden](http://katychuang.com/hakyll-cssgarden). This repo is a collection of themes I put together for a static site generator called hakyll. The build error says:

```
[ERROR] Missing field $site_description$ in context for item archive.html
```

#### A bit of background and dynamic values in template files

[Hakyll](http://jaspervdj.be/hakyll) written in haskell and the only package I am aware of (as of May 2016) that is available for generating static sites from markdown or latex with Haskell. There are many other options that allow you to blog using the Haskell language but for the idea of converting text files to a site with consistent theming, this is it. What I want to focus on explaining today is the template system.

The template files are html snippets with variables such as `$author$` or `$body$` inside html tags. Most static site generators have a directory for `templates`, though sometimes you might see this folder called layout, or includes as well. The terminology mainly depends on what the framework author decided - in the case of hakyll, template is the default word. This can be changed easily within the generator `site.hs` file.

Each of the variables such as `$author$` or `$body$` refers to string values, that the generator will plug in with proper values. **Where do these values come from?**

1) You can save the string values as a metadata field at the top of posts pages such as:

{% highlight markdown %}
---
author: kat
title: cool blog post
site_description: an example
baseurl: http://localhost
twitter_username: katychuang
---
{% endhighlight %}

This is the easiest way in my opinion, but unless [you are using a template file that pre-fills the information](http://katychuang.me/blog/2015-09-15-transformation-tuesday.html) for you, it's easy to forget which meta fields are needed in your theme.

2) You can save the string value in your site.hs file like so:

{% highlight haskell %}
postCtx :: Context String
postCtx =
    dateField "date" "%B %e, %Y" `mappend`
    siteCtx 

siteCtx :: Context String
siteCtx = 
    constField "baseurl" "http://localhost:8000" `mappend` 
    constField "site_description" "my beautiful blog" `mappend`
    constField "instagram_username" "katychuang.nyc" `mappend`
    constField "twitter_username" "katychuang" `mappend`
    constField "github_username" "katychuang" `mappend`
    constField "google_username" "katychuang" `mappend`
    defaultContext
{% endhighlight %}

This approach hardcodes the values so that every file generated will have these metadata values. Note that you can save the values in another form of data structure as well, whatever you're comfortable with in Haskell.

The advantage of this method is that when any of these values change you only have to change 1 file instead of every single page. 

3) Lastly, you can save this information in a config file. It's probably the best practice as far as content management - separating the infrastructure from content and metadata. Do you need to do this for a personal blog? That's the author's preference.

Jekyll uses the `_config.yml` to save the configuration information, and [the example for this blog can be seen here](https://github.com/katychuang/5min/blob/gh-pages/_config.yml). I don't know how to read from files with hakyll yet so until then I'll leave the code as an exercise for the reader :smirk:


#### How to fix the issue

As you can see from the hackage docs, the `defaultContext` ([link](http://hackage.haskell.org/package/hakyll-4.8.3.0/docs/Hakyll-Web-Template-Context.html#v:defaultContext)) comes with the default set of values:

* `$body$`
* any metadata field (i.e. blog post date, tags)
* `$url$`
* `$path$`
* `$title$`

As you can see, the error message was about the template variable `$site_description$`, which is not included by default, so when the template contains this variable you'll need to connect the value to the generator using one of the methods mentioned above.

**References**

* [Hackage Docs](https://hackage.haskell.org/package/hakyll)
* [The Switch to Hakyll](http://www.blaenkdenum.com/posts/the-switch-to-hakyll/)
* [Hakyll Setup](http://yannesposito.com/Scratch/en/blog/Hakyll-setup/)
