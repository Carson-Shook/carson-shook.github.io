---
layout: post
title: Still Not Dead - Also UWP Stuff
published: true
comments: true
---

I guess I haven't posted in a while. Not here anyway. There really isn't very much incentive to because people don't ever seem to come to this site. Not really surprising. What's happened in my life since my last post? The answer: not much. I've stayed busy with work for the most part, but I've worked a little bit on some personal projects. I guess this will be another one of those data-dump kind of posts.

### Work things that I can't really talk about much

*If you don't care about work things, just skip this section*

So I just got back from a vacation last week (of which I spent all my time playing Stardew Valley), and I feel much better than I had been feeling. We have a lot of large contracts, and clients that range from a town of population of ≅ 500 to massive cities and counties with millions of people. I have been solidly focused on those big ones because most of the other OPs team members are not ready for such a large customer. I also have a close relationship with our core development team, so that helps. Unfortunately these kind of projects are seemingly never-ending, and I had just become overwhelmed by them. Taking a week off has certainly helped.

One thing that I can tell you, reading from a live file as it's being written to on Windows is incredibly difficult, especially if you are looking for specific *complete* bits of information in those files. Up next, reading from a "live" XML file...
It's little addons like that that our customers love that make it difficult to sleep at night. I have written the best of code and the worst of code when trying to create some of these features. I'm not even sure that there is a lesson to be learned in this drivel. I'm honestly just ranting at this point.
I should probably move on.

### I have a new MacBook Pro now

So I wasn't necessarily the biggest fan of the 2016 MacBook Pro when it was announced, and then the weeks that followed that were filled with more bad news that excitement fell even lower. 

Sometimes I love being proven wrong.

My trusty 2011 MBP finally bit the dust a month or two ago (has it really been that long?), and it didn't just bite it a little bit, it died very completely. I used all of my necromantic power to revive it, but the only thing that I could raise from the dead was the ancient Hardware Test (that's `⌘ + D` on startup for the curious). Had it died a month or two earlier, I might have been able to get it serviced, but unfortunately the 2011 model was added to Apple's [Vintage and Obsolete Products](https://support.apple.com/en-us/HT201624) list. Now, one of my fatal flaws is the base thrill of "the impulse-purchase" that I desire when I am in a panic, so what do you think that I did? If you guessed "buy the second to most expensive 2016 MacBook Pro," then you are correct! A week and a half later and I was unboxing a machine that would make me eat my earlier words.

My old MBP had slow read/write times, most games ran only passably (meaning around 20 FPS) on medium to low graphical settings, start-up took forever, and the fans would spin-up quite often. My new Mac is such a leap forward from the dark ages that I was stuck in. It may not be as powerful as people were hoping, but since I can run most games on high and ultra settings and get between 30-60 FPS, I'm not complaining about that anymore. The TouchBar was another thing that I didn't know how much I would really like it. There may not be many apps that use it well yet, but being able to press a button and pull up a manual page in a separate window is a feature that I will never get tired of. Needless to say, it was way overpriced, but overall, I use it every day, and I feel like it has all the performance that I need (until I build a proper gaming rig, anyway).

### Dungeons & Dragons

Remember that campaign that I mentioned 9 months ago when I wrote my last post? It has truly been a highlight for me. Being a Dungeon Master is incredibly fun and rewarding. It keeps me busy with planning, printing, cutting, pasting, writing, and—finally—acting. As of this date, my players are about to make a treacherous journey along The Trade Way, and this will likely prove to be the most challenging chapter for me to execute. It has many open-ended scenarios that will almost definitely lead to my amusement when my players surprise me with a thinking-outside-the-box solution.

### Finally, a word on UWP

One theme at work that has been tossed around lately is the idea of running our product on Windows IoT tablets. Windows IoT devices are a close cousin to a failed experiment called WindowsRT. In short, they can only run apps that can be installed from the Windows Store or from some sort of provisioning profile. That means no traditional forms applications. In Windows IoT these app packages must be built to use the Universal Windows Platform (UWP), which is Microsoft's attempt to unify all of their many platforms, however it also means working against the lowest common denomiator. There have been whispers and mumbles about the topic for a while, with the conclusion being that doing so would be about as close to the meaning of the word "trivial" as an angler-fish is close the the International Space Station.

Just for fun, I decided that in my free time, I should try to make a little mock-up of out application to see how difficult it would be to recreate it using UWP. It was surprisingly easy to create a simple proof-of-concept that demonstrates that the functionality that we need from the UI is mostly all there, and what isn't we can work around. There is one feature, however, that is currently missing from the UWP framework that fully prevents us from using it for now. `Assembly.Load()` is unusable. 

I don't just mean that `Assembly.Load()` is glitchy, or something like that, but rather that it's not even supported! If you try to use it a `NotSupportedException` is thrown. Our application depends heavily on being able to load and unload certain modules. It also drastically reduces its memory footprint. Until Microsoft supports the functionality in UWP, there is no way that we will be able to use it as the framework for our product.

So that pretty much sums up everything interesting that I've done recently. Oh, and I released a retina-compatible Dark Mode icon for Adium if you use it. Go check it out in my Projects.

P.S. I think I broke most of my permalinks.