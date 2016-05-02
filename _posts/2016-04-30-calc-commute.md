---
layout: post
title:  Citymapper for calculating commute routes
date:   2016-04-30 10:31:51
category: 
---

One of NYC's favorite pasttimes is picking an optimal commute route, based on time, amount of walking, number of transfers, and some other trivial things. I was looking for the hopstop website (used this 6 years ago), but it doesn't exist anymore. Citymapper popped up in search results so I took a peek. Turns out they have super awesome UI features like showing calories burned, fare & commute times as well as a lightspeed option (*scroll down to see lightspeed*) 

![](http://www.autostraddle.com/wp-content/uploads/2013/12/citymapper.jpg)

This afternoon I'm performing in a show up in Harlem then later in the evening need to catch a musical down in Theater District.

![My route](https://lh3.googleusercontent.com/kFsXjwpWgiuYrand_rsRyXioqQDk8coWNMbumlxokHYMr39IDTiuUmPyb3bmqD8EWduulmKEUboig_l4BfnVSIkNz0wPMkKif2wGtGbKxZzcih4I3oH_x-KSb8FXdmjNNA1UmIPd053BcFew8o72K1LAmIk7ooLewTZVZPsfpFQi30lQ-6i-ZaXZKIor2nn2_NXjqN7FMP9yGZ4pnz0pjJNCPtMp0HbSs6NUN59dig_xizZ7zzTQuKtUoiCJ0khxXYa1hx5gstKSnNK1X69StDH8lj5MPZQYFjeTYOoKRLXvHx_vqFFeJRFET0KXmerg5jFBZ7ZhWHzXBxNyi5FDsm5cqohW117aQbSFDB_TbWCJ06ArGQosPEOjTwHI5V8DfepUVc25a6ZyRlMtQgSKkRA6s-pTcab0IjZhDbaRxz420Y2BLX8pA9befyobFSg-8Wx5zWDPsAjcj0Nr2VZFU0hk0qkBrqgRG3Qp4rrgJjl0tPgN50idipLqre1CPhLV6QUVHqnPJD81YY2oxvjxRT8JvfZX8hNlGJkz4zQsOAhBSMouKxfIs5Fgv7NUKDH-AeWo6w=w1274-h844-no)

Took a peak under the hood to get a better idea of this app in how they render the UI. 

![Inspect Elements](https://lh3.googleusercontent.com/-dehdQ9junOA/VyegbDtLXLI/AAAAAAAAcqo/Ds8QTUzk8xoZ_l8NmB844N1TAtQPgSh_QCCo/s800/Screen%2BShot%2B2016-05-02%2Bat%2B11.15.08%2BAM.png)

Also of interest was the network panel in Chrome Developer Tools, it measures the network performance of a website. It took 10.21 seconds to load 1.2MB and 286 requests, which is [average loading time](http://www.seochat.com/c/a/Google-Optimization-Help/Average-Page-Load-Time-of-Top-Ranking-Websites-in-Google/). 

![Network Panel](https://lh3.googleusercontent.com/-3bx1sPpujto/Vyef2X94HoI/AAAAAAAAcqg/hv4qSdaeYHM_Aen_V_ehvJpwZrbCODwAwCCo/s640/Screen%2BShot%2B2016-05-02%2Bat%2B11.22.11%2BAM.png)

And then I noticed... when you load the page with chrome developer tools open, you get to see lightspeed directions as well :smile:

![Lightspeed!](https://lh3.googleusercontent.com/-jNMEY6FvmaM/VyefIjy2-CI/AAAAAAAAcp8/AK5iFUqh3oU5_rP0QKSE24F6neaUBYM3wCCo/s800/Screen%2BShot%2B2016-05-02%2Bat%2B11.31.08%2BAM.png)

<img class="emoji" src="https://lh3.googleusercontent.com/-v-t8U7H0c1w/VyefqODUu6I/AAAAAAAAcqY/ACJFYrtCdDY_jUQXu6mAWslszr7rGKS4gCCo/s800/Screen%2BShot%2B2016-05-02%2Bat%2B11.23.42%2BAM.png" style="float:left; margin-right: 20px" />

<img class="emoji" src="https://lh3.googleusercontent.com/-L1mthUezcSs/VyegF5louOI/AAAAAAAAcqk/kmLThqh-ZPw-jD14xqVrRzrRCr2OocztQCCo/s800/Screen%2BShot%2B2016-05-02%2Bat%2B11.24.10%2BAM.png" />

I looked up more information about this company and to get a better idea of how they create this product. First stop is [Crunchbase to see their profile](https://www.crunchbase.com/organization/citymapper-limited#/entity).
They recently raised $40M funding and explained their process on their blog: [From A to (series) B](https://medium.com/@Citymapper/getting-from-a-to-series-b-883393164276#.rhopijmn0)

Their software engineer job posting describes, "We use a lot of Python and some C++ and Java" and their map and commute data comes from [General Transit Feed Specification (GTFS)](https://en.wikipedia.org/wiki/General_Transit_Feed_Specification) and [OpenStreetMap](http://www.openstreetmap.org/).

Up until this point I had only known about [Transitfeed's](http://transitfeeds.com/) archive of GTFS feeds... so glad to know Citymapper already built a bunch of awesome features!

*This post was not sponsored and is not affiliated with CityMapper.*