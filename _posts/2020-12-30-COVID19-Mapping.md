---
layout: post
title: Fighting against COVID-19, One map at a time
---

Seemingly overnight, [@dogryan100](https://twitter.com/dogryan100) (Ryan) and I have joined the fight against COVID-19 in New South Wales. I wanted to share my story up until this point and highlight the challenges along the way.

### What am I talking about?
For those not in the know, we (Ryan and I) are two young South Australian guys with a keen eye for news watching and data analysis. As a response to the Parafield Cluster (South Australia), and now New South Wales (NSW)’s second wave, we have developed, maintained, and promoted Google Map maps visualizing government health contact tracing locations on an easy to use map with location markers, based on the Google Maps software. If you haven’t seen them before, you can find them [here](https://www.google.com/maps/d/u/0/viewer?mid=1JQbZuMafdwgQMGgs4cGKuONrLh5dFEPj&ll=-27.263446073695118%2C134.0334638381329&z=4).

### So, how did this all begin?
Starting in May 2020, Ryan began posting [SA COVID-19 News to /r/Adelaide](https://www.reddit.com/r/Adelaide/comments/gfm145/timeline_of_easing_of_restrictions_announced_for/). Over the coming months, Ryan would earn a strong reputation as the COVID-19 Marshal of the [/r/Adelaide](https://www.reddir.com/r/adelaide) subreddit.
In November 2020, SA experienced the Parafield Cluster. Ryan wanted to understand where the many contact tracing locations released by SA Health were, so I suggested him to create a Google Map. Very quickly, this map gained traction and became a useful resource in mapping out contact tracing locations for SA residents like us. As of posting, this has totalled 170k views.

December 2020 seemed to be smooth sailing for Australia. The Victorian second wave was over, Christmas was near, restrictions were gone, everyone was happy.

Then, the gold standard of medi-hotel programs proved to become anything like that. Right now, NSW is facing a second wave with the potential to be just as chaotic as Victoria’s.

From the start of this second wave, Ryan created another Google Map and began the work of mapping out hotspot locations as fast as NSW Health could announce them. I quickly joined in the fight and became a contributor to the map. I focused on spreading the map far and wide, teaming up with COVID19Data.com.au and the amazing Juliette O’Brien [@juliette_io](https://twitter.com/juliette_io) to assist with the distribution of the map with a strong social presence on Twitter. As of writing, we have just cracked 400k views which is simply mind-blowing. 

This brings us to today.

This second wave is not even close to over. We have learned many lessons along the way in these past few months and weeks, and all have developed a better understanding of public health crisis communication management.
The rest of this blog post focuses on a deep-dive analysis from specifically mapping the NSW Contact Tracing locations during their second wave (December 2020).

### Getting our priorities straight
From the word go, we knew we are developing a public health information tool. This is not a map of holiday destinations; this is a map of locations outlining areas were a potentially deadly disease were spread. It doesn’t get much more important than this. We fully realized quickly we must put as many steps in place as possible to ensure the data uploaded onto the map was accurate and done promptly against NSW Government announcements. This is easier said than done.

### Developing a workflow
Early on during this second wave, we realized that compared to the Parafield Cluster, this one was going to be much more complicated. Apart from not even living in the state, we had to deal with many more sources of information from government entities we didn’t even know existed. 

NSW Health initially created [this dedicated page](https://www.health.nsw.gov.au/Infectious/covid-19/Pages/case-locations-and-alerts.aspx), which then promptly crashed a few days later. To get around this, they created a [secondary site with information](https://www.nsw.gov.au/covid-19/latest-news-and-updates). I refer to these as “NSW Health Contact Tracing Locations” and “NSW Government Contact Tracing Locations”. 

For the first week or so, a daily circus of Twitter reading, news watching, and word of mouth listening would happen as we tried our best to find and monitor for changes and announcements. NSW Health (understandably) scrambled to develop a consistent line of communication, meaning we had a moving target to hit. Every update was processed manually, by hand, leading to time delays, confusion, and frustration. 

During the middle of December, I realized this was not smart and was inefficient. I went to work creating and implementing an array of automated tools to produce the end goal of a stream of notification-based information for Ryan and me to be alerted too whenever anything happens.

(It’s a Discord channel with a few bots following Twitter accounts and RSS feeds. We also have one secret weapon).

Arguably the most important tool we’ve used to date (during the Parafield Cluster and this one) is [Visualping](https://visualping.io/). Using this tool, we monitor key websites for changes at very common frequencies and get notified whenever they happen. This is useful to catch changes before (or if) they are announced. This includes new locations and updated advice messages. #NotAnAd

By this point, we had a much more established system of tools. We had the motivation, we had the notifications, and now we needed the data.

### Dirty data
For most of the second wave up until mid-December, map updates were done entirely by hand. Every tweet was decoded, every website update was copy-pasted, all of it. By this point, I had enough and wanted to smarten things up. During this process, it led us down a windy path involving everyone’s favourite activity, working with dirty data.

A strong contender and eventual winner to become the one source of data was the NSW Health contact tracing locations page.  As a daily consumer and close watcher of NSW Health’s messaging surrounding contact tracing locations, it was clear they are pushing people to visit this site. A nifty little feature of this site is how it uses JavaScript’s Data Tables plugin to display the data. This means with a click of a button we can export the listed tables into various file formats. One of which (CSV) Google Maps accepts and processes with ease. 

We quickly realized this meant we can do away with manually entering data and implement this semi-autonomous system of downloading data and putting it into Google Maps. This was working well for a few days until someone messaged Ryan asking why a particular location from the NSW Government contact tracing page was missing from our map.

Uh oh. Calm turns to panic, followed by confusion.

It is at that moment; we learned those two government pages contain different pieces of information. Not by a lot, but not nothing either.

We spent quite a bit of time looking into the problem to understand what was going on and, as of posting, this problem has not gone away. Both pages contain different pieces of information, leading to confusion and mistakes. I knew we had to draw the line in the sand somewhere as it was clear quite a few people use and possibly rely on our map for public health advice.

I decided that the NSW Health contact tracing page should be classed as the source of truth. This was done for two reasons:

 1. It is consistent with public health messaging of where to look
 2. It is much easier for us to update the map based off this page (meaning faster updates with no real possibility for mistakes)

For reasons outlined later in this post, I strongly believe reason #2 weighs in importance as much, if not more so than #1.
To help us with this new source of truth approach, which we wanted to be transparent about, this was documented in the form of tweets to NSW Health about data issues and in the map’s description (alongside a pre-existing disclaimer). We also made a rule that any other social media/community sources (such as media reports or Facebook posts from businesses) will be ignored until NSW Health acknowledge them. We are not a large enough team to handle rumours and speculation. We are still two guys.

> ❔ Why are locations missing? If NSW Health have not published it here:
> https://www.health.nsw.gov.au/Infectious/covid-19/Pages/case-locations-and-alerts.aspx
> ...we will not publish it (typically). We are aware of clashes with
> this page, but we are ignoring them:
> https://www.nsw.gov.au/covid-19/latest-news-and-updates

Alongside this change, we had a suggestion to implement a digital change log to assist with audit trails. This is available on the COVID Maps website, linked prior.
Since making this decision and change to use a single source of data, even when conflicting data exists, I still believe this is the correct decision and the way forward for us. 

### Other Maps
I will take a quick moment to acknowledge we are not the only people doing this. I’ve had a few other Google Maps sent to be on Twitter, which do have some stark differences than ours. For example, [@AudreyData](https://twitter.com/AudreyData)’s [map contains very impressive public transport route visualizations](https://www.google.com/maps/d/u/0/viewer?mid=1xX9bqq0TGONy2WII6tR1pilI52XFydcw&ll=-33.8198455148036,151.12601896278926&z=16).

Recently, [COVID19NearMe](http://covid19nearme.com.au/) was launched. I think this is a great resource to be used as a checklist for residents of NSW, but please note at time of writing it does NOT contain any transport locations. 

You may ask, doesn’t NSW Health have a map of locations? 
Well, they do. However, it’s not exactly helpful and is usually never up to date (days at a time). This was a catalyst behind the creation of our own map.

### The personal toll of this work
I am open about my mental health (which I believe to be in good standing) in person, but never in a public forum like this.

During the weeks before Christmas, I attempted to jungle my day job and updating this map whilst Ryan was unable to take over. Even with all the tools in place, I still found this consuming most of my days at work (with the boss being okay with it), however, it became a constant stress. Late nights in the office of Twitter surfing, going home to spend more hours on Twitter following COVID news, late night location updates and minimal sleep resulted in an extremely self-induced anxious period for myself.

Since Christmas, I have tried to step back as far away as possible whilst not neglecting this map. Ryan has been gracious enough to resume the duties of being the primary person responsible for this map, and I must say it has been a burden lifted.

Looking back, I am surprised how quickly this project  (combined with everything else happening at the time) spiralled my mental health. The stresses of ensuring nothing is missed when dealing with public health data from another state is one unmatched to anything I’ve experienced in years.

Don’t get me wrong, this job is still not easy. It has its moments of stress and worry, and I am not even doing half the work compared to other amazing people in this community (see acknowledgements). I’ve put steps in place to reduce the stress triggers this job brings to the table, and they are working.

It’s important to put yourself first. 
Never forget that *(even though I did)*.

### Lessons Learned
Let me summarise:

 1. Working with health data is hard, especially when it’s from multiple conflicting sources
 2. When dealing with public health data, you must get it right
 3. This job is stressful and needs to be managed carefully
 4. Google Map Maker is fantastic at making maps
 5. Twitter followers and retweets don’t pay the bills

### What’s next?
We want to explore how we can advance the map further, including enhanced public transport routes, sewage detection highlighting and an expansion on the local government area outlines to potentially account for localized restrictions.

We will see what makes it into the map, or what remains a want to do but can’t or won’t.

### Acknowledgements
This map’s success must be attributed to the following people:

 - [@dogryan100](https://twitter.com/dogryan100) – For doing the hard work 
 - [@juliette_io](https://twitter.com/juliette_io) – For distribution and support of the project and concept throughout (we’ve had many messages and phone calls!)
 - [@migga](https://twitter.com/migga)/[@Covid19NSW](https://twitter.com/Covid19NSW)/[@COVID_Australia](https://twitter.com/COVID_Australia) - Constantly retweeting and assisting with the distribution and information on the map where needed
 - Everyone else on Twitter who liked, retweeted, or shared the map 
 - You for being awesome enough to read this post and hopefully sharing the map to your friends and family
