---
layout: post
title: hakyll css garden-ing
date: 2016-08-21 14:13:11
tags: haskell
category: haskell
---

This weekend afternoon I spent some time weeding [the garden](http://katychuang.com/hakyll-cssgarden/gallery). Tongue in cheek statement as it's a digital garden! :smile:

Tweaked the main menu and updated the about page to include some testimonials. I'm glad that folks find the collection useful and of course want to share their happiness. It feels great that my contributions are valued, even if I'm just learning as I go and unable to devote full time attention to this project.

Finally added another theme to the gallery. Been waiting some six months or so for a copy of the preview thumbnails as my workflow of capturing with PhantomJS couldn't grab a proper screenshot with the stylesheet working correctly with headless capture. Fast forward today I discovered that with Google Chrome Developer tools *(I'm on [v52.0.2743.116][2])*, I could easily capture screenshots of the correct resolution. 

As you can see it's there in the screenshot below. A meta level screenshot showing how to get the correct resolution: 

![Preview](https://lh3.googleusercontent.com/u8ElJd_AWdc34aqSMR5pOdtesW5l8JZneNzynud3wpKr2h6CZQatRsMXQSafKJlTptHzBJiZDrXOLpx2q3Nh56xQNH4m9saB4Q85MoI3MBjfyd3Dh8ubQjzEnNWCwWw0HhTTyKM77CiVc5oHn4Um2zlaoqH9o5I7czgpJx9Q7CTzG3aOmEGpNXTIVeC-IYkIex3yhs0O0SBFsIGIl83i-T3aVM5Aco6Vsb0Q4vNnZqnfdebsN7G9XWd4EeGy_YWZGp9v2xXqPaJSK9LHkCz8EK9qzHzePgoQSzz6-d95WJVCQzdGPX1eNXDO0LMzlyDyTKjJryXBG8i4H7p1AphFKB4-uGsXeK3zvfmHwqMsQ7V3wf4uCk6nKbqdRUTaZ9VYz5vnkvzpA5UNrKcLtE_3C2NaG0BCFggkaanb0eRSbtSLVMFvIOaX1Alvy4ZfqIHQOwkVx0Tx7At_LdS0f0wxOdPoa-6o70R88DtEYdm1rhPnNFbm3zVbD-S5VGiLhpzDeE2KZmegALjT1LcdyOu0WwVkl45EfCxPJm-DMknfC_bQkjdC441WymKgSMH_1zIzxA6gmBANnY41o_Wgu78kQb8aonY5wtTh=w2218-h1388-no)

With this feature on you can adjust the settings and save a device setting for easy reference later.

![Preview](https://lh3.googleusercontent.com/kjLIDZ7xEFNOAVZpTQaJ4G8Z4XNmQ2ae6iBTb3ne5SKzknvwrGRCa7DSNZVTDYFhabTF_g-uO7FMvO_CrAz3mZP8rWQJ6nXRdBWWuzUxNx5GXJjJ3yD7Com6Y6iZkxBuKLzBSnKSLmNiiKArCgAasAJh2mul4TpO1-9b9AELuFJNR0v5BfsVPoriN7Ptj12B8gUypthtRbQurHri3swK6iGKw24hR5jCL0-d9mZsOsqW2utF4-JYr8cqBV8ZiYpw5AirocCAUjwesRthYKAOWJ7miaz_LuVGsOa4gX4yRWq6uQUqKXzyJoiHbnRn2W5-XZhj9Ac4qnpm0HdVIlYTE-RHND9LkN2YRI66poYO1wYvpDaiyfFFt9HKPI_IJD89_vpjAjQMk3MM4l2XWsvZKhNKkyLgClz3Of0jrIevoiMZWXy-MzXSFJJTY2Y4Me6-qav_nsm8miIr02jbfY5A4fqELDq2raZSuBIxtwnbvtAcH_2cuRzktToc3ixA8O7c0x7cO08iTeBrc_p36tN129qRhFajMkwMhF37TDe8cqYOg2KpjmTZDAxkUojBkLRUBZx37hqfHRw4EVNVNggbDdzd78YObqYx=w1772-h1236-no)

And if you're needing to send this preview off to someone you can easily do so by selecting "capture screenshot" from the menu.

![Preview](https://lh3.googleusercontent.com/jcBplbDQFWE6UjcwlDlok0HV2vPfIZpbZ2oiSVpPK9zWLEDNB-jjSFrqQF85tMC9OLB_0X3MLZvemyzF5ELHz3mjsZ8Ui0Bjd-RhRgp_wOnmgS-BIUBsc9Kfr5taTH6-SB-ZAUMjclfu81mCRf3wKxp5Y6EGlb2KDev9bwBrAHOqdbPTEMT9XpxtJTnGdQJe6uGJNvkjnL89bto0ysGar4oHlQF_XkEpKGUoTCgPpP2u0YaspHBsUggWyHTHTdHzn3HfJbm8mEAbwqMpZEEB0JlBZfmqZFqLyDhInbBoB80ircrdhHoG4QSUUn0tIV59EprcinLPIR--X8Pg-B6Qxnq5nT3bwvxuIhZd0WZxSRMKf16p9U-uJnxB5fDa-YvKZD-c7dzm2tqk7zBFShSbLPVk6WKruNfTkhNG5w00BzfdkfJCDF_NBpFc0Pdsaxvg17iIjtXkN4zViM65qMeCdSNfXMmOI0bU9bjpJTvZ2ivsOT7LGZkeez5RyRd5zdflX23cTV9JiWEnKKT0oP5uekK5DQEwhozlVksWyezKi1jV68PpClhKDViKnO0xm7SyGJSQ4ZzplnYI2e0C8RpOhv0vfvMHXwuz=w2938-h926-no)

*et voila!*

By the way, I've been noticing that this month chrome has changed their design slightly with new default font, default link color, and overall coloring and margins of the application. Seems sleeker though I haven't come across documentation supporting this yet. Doesn't matter, loving the latest version.

[2]: http://googlechromereleases.blogspot.com/2016/08/stable-channel-update-for-chrome-os.html
