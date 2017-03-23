---
layout: post
title: Making of a Developer
published: true
comments: true
---

Well, well, well. It finally happened. I had to bite the bullet and pay for Apple Developer membership. It's not a big price to pay, and it's not like it will go unused, but more on that later. This post is (mostly) about the journey that I had to take to get there. But first, a little history lesson on how I got here.

### A Little History

BetterPonymotes (BPM) is a browser add-on that sticks My Little Pony emotes into reddit that only other users of the add-on can see. It used to be a userscript, and eventually that went away. With it went support of Apple's Safari web browser. After waiting for a while, I decided to pick up the project (it's open source) and I created a port for Safari using a free Apple Safari Developer membership. In June of 2015, Apple combined all of the their developer programs into one $99 per year program, but that unfortunately included the Safari dev program. This meant a lot of things, but the only important one is that I could no longer get my Safari developer certificates for free. With mine set to expire at the end of March 2016, I thought that I had a bit of time to figure things out.

There is one more piece to this puzzle though, and that is the [Apple Worldwide Developer Relations Intermediate Certificate](https://developer.apple.com/support/certificates/expiration/). It expired on February 14, 2016, and because certificates are such a convoluted beast, I failed to understand exactly how that would impact my developers certificate.

### That Brings Us to the Present

On the 25th of February, an update went out for the core branch of BPM. I had been playing *Kingdom Hearts: Birth by Sleep* all that day, but when I eventually noticed, I went through the usual routine of updating my repo, compiling, and then previewing/building the add-on in the extension builder. To my surprise, Safari told me that my certificate was not valid. I checked, and—to my surprise—the old WWDR cert expiration had taken my supposedly valid Safari cert down with it (I think so anyway. It wouldn't really matter in the end anyway since I'd have to renew in a few weeks anyway). So began the journey.

First things first, I had to fix my name. Even though all of Apple's other services have my correct name, for some reason developer.apple.com had my father's name on record. This probably had to do with his credit card being the first card tied to my account from way back when I first signed up for iTunes. This seemed straight forward enough.

![Email asking me for my ID](/img/makingofadeveloper/supportemail1.png)

Soon after, I received another email saying that everything went though and I was good to go.

![Email confirming they got my ID](/img/makingofadeveloper/supportemail2.png)

So I attempted to sign up as a developer.

![Email confirming my purchase](/img/makingofadeveloper/supportemail3.png)

So far so good. But then I get the following email:

![Uh Oh. I thought my name had been sorted out already...](/img/makingofadeveloper/supportemail4.png)

That was not what I wanted to hear, but I expected as much. For as much as Apple does, they are only human, and server equipment is only metal and silicone. So I sent another support request in. I suppose that this would be a good time to say that it was around one work day between each of the support emails. The problem was that I had un uncanny knack for sending these requests in on the weekends. So it was a little while before I heard back on most of these. At least they told me up front. Unfortunately the email I received was not reassuring.

![Email addressed to my dad](/img/makingofadeveloper/supportemail5.png)

It seems that someone (or some server) didn't notice that my name had been properly updated. Unfortunately, I couldn't upload another ID because of how recently I had just done that. Fortunately, my reply did not fall on deaf ears, and after explaining that he had the situation backwards, he got things sorted out.

![Email where everything got sorted out](/img/makingofadeveloper/supportemail6.png)

Well. That was good. I'm glad that it didn't turn into some other big mess like I've had with some other services. Finally, I received the email I had been waiting for:

![Finally, I am a developer](/img/makingofadeveloper/supportemail7.png)

Finally a developer, I can finish building this extension and be done with it, right? 

### BUT WAIT! THERE'S MORE!

It turns out that the current version of Safari doesn't recognize the new WWDR intermediate certificate, so even though I had just renewed my cert, it did no good because Safari didn't know that it existed. Turns out that this is a known bug. Fortunately, there is a version of Safari that does support it, the beta build. So using my newly acquired developer authorization, I opted in and prepared to install the latest beta of OS X El Capitan. Before doing so, however, I decided to to a disk check to make sure that I wasn't experiencing any disk errors before attempting this. Turns out I was. Fortunately they were reparable with a quick boot into the recovery partition. Turns out it was choking on an old El Capitan installer.

Things are running much more smoothly now. Still, I needed to get a good backup in before switching to a beta branch. Unfortunately I had the bright idea of trashing a backup that seemed to be stuck. I had done it before without any problem, but I guess I caught this one in a weird state. As some of you may (or may not) know, Apple does not use a physical folder for the Trash. Each user/root of a disk drive has a hidden *.Trashes* folder, and the Trash is a combination of all of those currently mounted disks' Trashes folders. Unfortunately, OS X does not seem to be a magic bullet capable of deleting anything. Even `sudo rm -rf` had no effect, so unfortunately I had do nuke my Time Machine drive. Delayed yet again, I decided to just let it backup overnight, and I would deal with it in the morning.

That's what I did, and it worked out just peachy. The current beta installed without a hitch, it's very stable, and the add-on built just fine. It was a lot of hoops that I had to jump through, but overall, I'm not mad. Apple dealt with my requests more quickly than most companies would, and after all of that, I finally found out why they charge $99 for membership. The resources available to devs is bottomless! There is so much to learn from the official resources, and I've learned so much already. I think that I'm going to enjoy finally trying my hand at iOS development.