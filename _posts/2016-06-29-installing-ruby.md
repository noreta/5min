---
layout: post
title: installing ruby
date: 2016-06-29 11:57:35
tags: 
category: 
---

Attempting a Ruby version of the spiral algorithm, to get used to the Ruby syntax, for later getting familiar with using Rails for app building. Was recommended to use Ruby version 2.1.5 from a reputable source. Had an old version ruby 2.0.0, can't remember where it was from. Probably came with the laptop or installed when I needed brew months ago?

#### Installing RVM and Ruby 2.1.5

I found which version I had with `ruby -v` and then found where it was linked using `which ruby`

From there I installed [RVM](https://rvm.io/) first, then used RVM to install Ruby. 

Install RVM with `\curl -sSL https://get.rvm.io | bash -s stable`

Then you can install a specific version of Ruby `rvm install 2.1.5 -C --with-readline-dir=$HOME/.rvm/usr`

The results take a while, I stepped away while it was installing.

![Screenshot of installing RVM](https://lh3.googleusercontent.com/3bzd1HDyuPUt7a6tm1sZdXZai-RT1Jtywo3G1abL9W135loq35Owix-xf9XJ4e25-5EJCWqRQqSiul75odQVtn7mvEo5TZNLuixYxCHiwrYGQ6BBBtZHeDOwJ--ztzeCPSqAn8u1YKDFcWOkx_Z5LtyBb-PU2Qg8UCL7_IIWCSYpXxhO7PbEcP8HfC37aIbtsSgVdqWmrXotZlVYNkQ49lYauSBJYDmt8PGU3oNxxsvEjWCNJX-IG7WXGf6wm3vvX0BVPXV3ahwshxSFzBcJNRTb_y6tO8-FFNf0RnSQR7QAFdz4pTM6rfz6B-SuB_s43jBCsSpjNffFnrSXyoz2DM6FrU4SSMxiK93qz5Aeeekbtx35OyVWO_j_kHMwhew54T-sE19n0Yk_B1jWLB5tMZFxTNaXmS5q_LKmDHH0fMr3DFVZrDvG-_NQFy-BvINR3QrlCDgkc_ll8l-PqlbkvxT8Y4ZrtbZSj_54O-ODgPgq-rm9MPViWwKDhKIE97syN2x1PhDIF7BWKZJlyoDJCr9eT26ErHi4nW0USN4vvSpkbwGZG_nPLpjbg70lyi8JSSSe10jxY761AHD74kLUg1ECDYWZ7YGD=w850-h832-no)

In the end I still had to fiddle a bit to get the right ruby version in my environment path.

I moved the original Ruby to `/usr/bin/ruby2.0` in case I need it in the future and then created a symlink `ln -s ~/.rvm/rubies/ruby-2.1.5/bin/ruby /usr/bin/ruby' 

In a new terminal window, `ruby -v` will give me the version I want.
