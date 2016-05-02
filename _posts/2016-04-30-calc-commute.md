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

![Inspect Elements](https://lh3.googleusercontent.com/5_BzF8ZRVFL4JMvtkxdaVmNcVHtu28RAnmnqaRQLZqrOHu2Tr6AzLfWtV0tzSxaeJHQK3kFoAGw9Vjto_ayzlnKcui4HUZgV0qCWdhcRQYIItmUjdA7iK0ZP0oUXWfwd7gXvsywvVTx1ZsZ-oBqntMbU6ovuJDyESmN-qudIwEoGA76lz003M3Ye5nuNO8YLgwTiy2wSV9kEnzj0zWbGXAhj420gdSeTinvmSF5X_LzCssCnL3sJbyBV6qF-yvaLFZI1Z6U2W9F20Tw_i04kamKGLxc7GH-kMHJW3I_z61uJv7E5KbvLkMk5-eQuE4oAt6jH2NRS9ZEomD14gkLS3PPf1KiyU3gDMQK0mUJhSyFFFoPUHZf3bxMsvMJqFNgSkPTuYscXOBboL0-ToXoLfa2pqmky6TG5naUEVW8SAUx26gz4Unf-eXR46LLKBqkVFSzLkW4wyJeXNIcYvBbbxmazTFNCg6s36Gf_515jFisxy6LEi8ateKygqSpLssJHQsL0fCFtFwnTc2vNNIsNuvchSfBZy2oKZABH2VQ9AZFgVt6OA4nusIkQchHRVBAB8iWT1w=w1265-h787-no)

Also of interest was the network panel in Chrome Developer Tools, it measures the network performance of a website. It took 10.21 seconds to load 1.2MB and 286 requests, which is [average loading time](http://www.seochat.com/c/a/Google-Optimization-Help/Average-Page-Load-Time-of-Top-Ranking-Websites-in-Google/). 

![Network Panel](https://lh3.googleusercontent.com/ckmddj6HA-BwNOXFp4XdYIlmodI-csKe0aNcnRlq-J6sg3_OQ6U7EdewDPHnDunUJJQBEMZtQ4IGSIgLqOrXFj-SOE8WSPlh6eLRRvmTpDfLN7URvlvZf2PavWTPx7UO_NjBOJH8b1943VwDy-2rJgSVICdA0w2Bf4SQldJUUTcGzueR5zeJ8STjGNggskzf1EGoLssA7u0bs_S18VqX2QOIib0fRnYaq90pvPB4jn5Q5_A-OUfrfJxHWQ-l9FVA6XO1hYi417djjYuIiCVaYCdEDo6FdNL-Nh3CoMek3NmlSFXnGqr2z8wo3iQ7uRBEg_lEFm5FiHgDh8Z1D8KZVzK4WG2a805vfGn5fePS7FvIKJckTtcP8KcSgYks-EAIz8qKAnUkRA38-st2KXdlt6TAI2TvratizEkZHS1ie-aYfGdrIp5vZK7OU-PIWRy-IJWaT4CEtm0icRJux9Vo0UbSKk0o9GuiZWCCcToJOXXqVox9XhgWdtppLvfLZxbcvkhJfc5ouDtTWrYerh6wZp0VLHODqK0DBhpU8Y2h9fS2dI6gSaQ3t9Y8qQzyMSsKz1Hc8w=w1121-h975-no)

And then I noticed... when you load the page with chrome developer tools open, you get to see lightspeed directions as well :smile:

![Lightspeed!](https://lh3.googleusercontent.com/uYK-skdUNeLjsUuSgxuozThySXof7QbYZlGwDagww1QlWt_gOiObIk2U3RrxEHlQFvmxQfgwikCsC3tkkzgz3xqWYmst4rpZVDuB4N-8Zn7Trk_bll-2fQ6qGyNqJ0DcSYzObbh-CEYalSlsRFcT6EtS_YqeEUXDaiqtbu9ie-EJEBt_k7RjUvGtCw8AnEYjDuUW4iivBLWAQcpPrBVUVkDZ61kTGs2MiVoFGVuiW2RNAiQcLdDtkXv8G8Xm-6MDE5uUd1H_YWXZ2G_y6QnzqdjX2X3CSGBxdYWDBX0ZY8gKGEyGu0Hsc4P7temC-r-e7fx-b2HZNT8EnLhLXrLPdcN5NF7tZo5BA_XHoUMM7uTszfxL0n5qN4ZFxl3Kre5ubCsdpn9pFn9S-1xwPHDiOMpHVbASx1l5VwVnuJ31N0GNAYb2ST0FMAXUysI75igvIJvAgnpfWGgbtz_XPE0M7oO5CXKdU6RLY5M5HkqlnDHNrpitt8YCVBDxlM84cLlrk-koaSh76TmwqDeKaPldBOOQHPh6QTP5QvbavSQGUGZdjSpeNNVqcaMPZEaJ9jpFKaH4Ng=w1124-h756-no)

<img class="emoji" src="https://lh3.googleusercontent.com/OoifgQT0KCnb3LKCylpgiyqnJY49FOEwVss6CWlXOLEIBBucyPG8Dk9acG5oHVX73fRnebL3v2K31RKhz95S698UPrwuLEDV1UogumtNFvBD99u6cmzovanw48H4INwWGsRqmhh_n1AyxMbZQyqxMCCECv8kUQdgSgb1qpMxqkQHEXdykCKHWsCh8OIVTyB_dIZlxUVg8bT8Gad6p1prfCHx7Jwogwvk_49Fn8RH1h_gbGtsea3DmJ2cFuxnaCvQIOX1GKJbHfWfV0Z9onTluunJ4Quzcgtt5_vS-Q60-cZXNfDt0AzBbvfE8ihcstfQDWO4FnArORVCbW9USJsjUgKHVKBWsP3wNyI6pWRwJpEkI9tCo_C201C4wzQHnQAABR-YSvy__AoIuMguqGALTDmoU7VpiH-WCw_RTpXdmIkW6t-HkDC3BA3ZYvjJOP4m-zsWrt0HLbx9mJbeCzFOuMeUQl5YJEtslpSBMlIJ1A1_vRaZT5_5jBJoOeVj1KUczf884yagkBjZL4ntomNK0jYX-Unw_cNRmwujDuvxCPKU3Nlc1-rx2zw0jbz-ypCnj82ltQ=w294-h220-no" style="float:left; margin-right: 20px" />

<img class="emoji" src="https://lh3.googleusercontent.com/scUB-Ak3-2EswdVFRTQL_pqKvKMfXmc36yW3GmEX76xV2zy_Yx4qJAt9kl8Cg7RbSZYS_htjZdDzXOvzYN45qhjb6E6bF782SCOMVW66k4CaNF7vUvAeuJICbGLJgmf6QHVzqsBISapH_BVflLFsaNDsPGLCXeG1aFhTrWz1EMVTTz11TaOBC95r1fj3IXByxLFJiJRP7W0_nq_G0uaUv-EOu63snkVo09NuaNVy4iJ2DlYc5LRuqg2Z3qmXqt2D0G5nmk1X9YgGYF9f0wIa_Egpi6yxo5UxOjebqn_oV3DCp_RWPawM0WOjxV2bpi0KDeT8S39ynZSURFHwj5kD-DxdCBeSZ8vq-XqOMqG2dYGSIySFvbF1epxG0oxjhBXzClKLbVMLj6WGppkpZPKtQa23QHjrjZxqoVmNUHJL8yojqPVABwrG8D7naibNvl4OBw2roOzUS-sz5GWosOpJOBVKrwtGvkLWZjJhgjXMoFJB4ldae2cTug9sJkFGTlEQOxnx68SpO6EfMocODctERBGORMChW9EQxFm_IO003qWSXKAOeX3ujoAdqlZzZ0wkSsJgKw=w330-h395-no" />

I looked up more information about this company and to get a better idea of how they create this product. First stop is [Crunchbase to see their profile](https://www.crunchbase.com/organization/citymapper-limited#/entity).
They recently raised $40M funding and explained their process on their blog: [From A to (series) B](https://medium.com/@Citymapper/getting-from-a-to-series-b-883393164276#.rhopijmn0)

Their software engineer job posting describes, "We use a lot of Python and some C++ and Java" and their map and commute data comes from [General Transit Feed Specification (GTFS)](https://en.wikipedia.org/wiki/General_Transit_Feed_Specification) and [OpenStreetMap](http://www.openstreetmap.org/).

Up until this point I had only known about [Transitfeed's](http://transitfeeds.com/) archive of GTFS feeds... so glad to know Citymapper already built a bunch of awesome features!

*This post was not sponsored and is not affiliated with CityMapper.*