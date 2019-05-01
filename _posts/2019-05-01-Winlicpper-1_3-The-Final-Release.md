---
layout: post
title: Winclipper 1.3 - The Final Release
published: true
comments: true
---

So much for that Winclipper 1.2 writeup that I never made. Whoops.

Today marks the release of Winclipper 1.3 which will, for all intents and purposes, be the final release of Winclipper. I haven't been nearly as active on this blog as I thought I would be (blame twitter), but at the very least, I should make the effort to post about software releases here (especially because I've become less professional and more personal on my twitter account lately). So, without further ado, let's jump into what this release entails.

### Adding the Delete option

One feature I managed to slip in was an often requested one: the ability to delete individual clips. Now you can right-click on a clip and a secondary context menu will appear, allowing you to delete the clip. Now that I'm using it, I wish I had implemented it sooner, if only I had known how at the time.

### Text preview caching

The formatted text previews are now briefly cached after they are created so that large previews will load near-instantaneously.

### Memory leak fixes

There were a handful of extremely tiny memory leaks that I have fixed. You probably won't notice a difference unless you've copied/previewed/pasted hundreds of thousands of items without restarting Winclipper, but now you can rest easier at night.

### A fix for the MS Edge hack.

I don't suspect it will be around much longer anyway, but I have made some changes to accompany modifications that Microsoft made to Edge in the Windows 10 1809 update. Now the hack is only needed for previous versions of Edge.

### Confirmations galore

Now when you click Clear Clips, you will be met with a prompt asking you to confirm before deleting everything. This should prevent accidental deletion (which was something that I did a few times while working on this update, thus prompting it's creation, so my misfortune is your gain).

### Bitmap support!

This release of Winclipper finally supports bitmap graphics (even with transparency), and displays them in the preview the same way that text displays. Plus it has a tiny thumbnail in the menu, along with the image dimensions. The amount of infrastructure that was required to support this was mind-boggling (at least for a project on the scale of a single developer). It is quite robust, however, and it uses a cache which dynamically loads and unloads images based on their usage to keep its memory footprint low. This was the final roadmap item that I had planned for Winclipper, and now I feel like it is feature complete.

![Demonstration of an image saved in Winclipper](https://www.carsonshook.com/Winclipper/imagepreviewleft.png)

### A final word

I know that there were several other feature requests that people have made over the years (namely, pinning clips and timestamps), but I likely won't ever be implementing these features. Personally, I have never used them in any clipboard application that I used prior to Winclipper, so my personal motivation to add them is low, and to be honest, while this has been a fantastic journey that has taught me so much about C++, I'm ready for a break. Not just a temporary break, but a permanent one (bug-fixes notwithstanding). When I set out to build Winclipper, I had a roadmap in my head, and that roadmap included Unicode text, bitmap graphics, and all of the other features already available in Winclipper, but nothing else. 

Recently when I've been trying to have fun with friends or stop and play a game or develop my artistic muscles, a voice in the back of my mind has been saying, "Shouldn't you be working on Winclipper?" As a result, I've just done nothing, and that's not a healthy pattern to get into. This was how I came to the decision to complete development on this project: It's no longer fun, it's no longer just learning; instead it's a second job. I've been getting much busier at work over the past year, and I just don't have time for large scale pet-projects like Winclipper at this time. So to all those who use it on a daily basis, "thank you!" This project started out as an experiment for myself to learn C++, and to solve a problem that I had at work, and now I consider it complete, and I hope that you will continue to enjoy it every day that it saves a piece of text that you didn't want to lose, or allows you to recall that image that you copied last Tuesday. I never expected anyone to use this software beyond myself, and I am truly humbled that you gave it a chance.

Thank you for everything.