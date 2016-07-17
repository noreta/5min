---
layout: post
title: photo metadata
date: 2016-07-17 09:34:39
tags: 
category: 
---

Learned that you can edit music metadata from the commandline. On OSX, you can use the `xattr` command ([xattr man pages](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/xattr.1.html)). Here's an example of how the command looks like:

```
xattr -l file.mp3
```

I wanted to change the cover art and couldn't figure out what the metadata location was for mp3 files on mac. So I ended up using an application called [Tagger](http://bilalh.github.io/projects/tagger/)

#### Update

There's another command you can use, `mdls`, which will [list all the file's metadata](https://www.macissues.com/2014/05/12/how-to-look-up-file-metadata-in-os-x/) ([mdls man pages](https://developer.apple.com/legacy/library/documentation/Darwin/Reference/ManPages/man1/mdls.1.html)). 
