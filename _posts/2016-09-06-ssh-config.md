---
layout: post
title: ssh config
date: 2016-09-06 22:39:29
tags: 
category: 
---

There's a way to connect to a server from the commandline without having to remember your username and password off the top of your head. Without having to resort to a password management software also. The way is using an `ssh config` file, saved in `~/.ssh/config`.

{% highlight bash %}
# contents of $HOME/.ssh/config
Host 
    HostName example.com
    User dev
{% endhighlight %}

This file means that you can type in `ssh dev` and log into the server. The first time you do this, you'll need to enter in your server password.

Next, copy the contents from `~/.ssh/id_rsa.pub` from your client machine and add it to the end of the file of `~/.ssh/authorized_keys` on the server machine.

`id_rsa.pub` is your public key, by adding it to the `authorized_keys` file it lets the server know you're accessing from a trusted computer.

For further information, the online [documentation](http://linux.die.net/man/5/ssh_config) contains the manual for using ssh_config.
