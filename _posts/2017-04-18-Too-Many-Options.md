---
layout: post
title: Too Many Options
published: true
comments: true
---
Something that I've come to realize is that I'm terrible at committing to a project. Reddit would tell me that this is the plight of every developer, but were that completely true, we wouldn't have all of the handy utilities that we use every day. What makes committing to a project so difficult? I have come to the conclusion that (besides boredom) the reason is due to the imperfections of every language. Given enough time and complexity, a developer will run into a language that doesn't support the thing that they need it to support. At that point, the options are:

1. Extend the language
2. Learn how to use a third-party library that extends the language (possibly using another language)
3. Give up

The choice seems pretty easy to make for personal projects if you aren't fully committed to them, and unfortunately none of mine have been anything useful enough to commit to, so they tend to fizzle out. I have learned a lot in the process, so it hasn't been completely useless. I've learned the limits C#, the UWP app platform, Swift, and others. I bring up the C#-based UWP and Swift specifically though for a couple of reasons. Firstly, These are both platforms that their maintainers are pushing as the new standard for their respective operating systems (and the systems that they have been ported to). Secondly, they both fall very short of older, more established languages/platforms.

Let's start with UWP. It's issues can be summed up in one class: `NotSupportedException`. While C# is an incredibly capable language (I use it at work every day), the Universal Windows Platform is not. It has the same sort of flaws that Objective-C had when Apple first started to allow apps to be written for the iPhone. It's an incredibly capable language that is horribly limited by what the platform allows you to do with it. Much can be forgiven as it is a relatively new platform, but there is one method that cannot be so easily forgotten: `Assembly.Load()`. Anyone who has worked in an enterprise environment understands the importance of modularity of design. Even a fresh CS graduate should understand that principle. Dynamically loading certain functionalities allows for fantastic memory savings if you need a "slimmed down" version of your application to run on a mobile platform, or just general snappiness on more fully-featured platforms if certain functionality can be unloaded when not in use. Until UWP either gains this functionality or provides a suitable replacement for module/library management, it will remain a toy that will only be useful be consumers, never by the professional world.

While this would be appropriate for small projects it does still put a damper on my relationship with the platform. Actually, more recently Windows itself has been putting a damper on things, but that's an argument to be made in a different blog post.

So what about Swift? Swift is good... when it's stable, which is increasingly feeling like never. In addition, just as soon as you have a project three-quarters complete, a new version of the language is made available that would substantially cut down the amount of work you just did, so you refactor, but now you hit an edge-case in the compiler (more specifically, it's usually the lexer getting stuck in a loop) that causes Xcode to panic and die. The process makes doing any work with the language a chore, and makes you question why you're not using Objective-C instead (which for all of the Obj-C calls that you have to make, you might as well be).

It's all very frustrating, but these dead projects have taught me one thing: Platform specific programming is a pain, but it's the best way to maximize usefulness for yourself and others unless what you are doing can be achieved through a terminal application. General purpose programming languages are much better at solving any problem that you throw at them given enough time and effort, but they lack the benefit of platform specific niceties.

Maybe that's just my personal opinion, but so far I haven't run into these same problems with C. Sure it may be more difficult to do even simple things, but I can eventually make it do what I want it to, and I don't have to worry about everything constantly changing on me. Considering a person can only get so far in life without needing an object-oriented language, I've decided that I should learn C++. Not only is it a very powerful language, it also has excellent support on both Windows and MacOS, and by support, I mean OS hooks. If I later decide to add  a GUI to my projects, then I should be able to do so with minimal difficulty.

What is my point about all of this? If there is a point, it's that language maintainers should focus on making useful languages, not just languages that are easy to use or read. Without reliable functionality, there is no point in using the language if the project is to be maintained over any measurable amount of time. There are simply too many options when it comes to languages that claim to be the only language that you will need for a project, but fail to deliver when push comes to shove.

Now I understand why the C/C++ standard is marked in years, not monthly build numbers.