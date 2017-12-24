---
layout: post
title: The Need to Archive
published: true
comments: true
---
I never used to really understand people who downloaded everything that they came across. I also used to believe that anything that existed on the internet could never truly be erased. All of that changed recently when a I saw a video that I had liked from the MLP fandom get re-uploaded to a channel that tracks this kind of deleted content. At this point, I paused and said to myself, 

"Maybe downloading all of your favorite stuff isn't so crazy. I got lucky, but what if that channel hadn't existed? Good thing that someone out there is doing this kind of thing for me."

So I found a utility for downloading YouTube videos and saved that one along with a handful of some of my other favorites. A day or so later, I saw a post on reddit stating that the channel had been deleted, and later found out that it occurred because of the title of a video the channel had in a playlist contained the phrase, "New Lunar", which had recently been found to be a title that was being used to smuggle illegal content through YouTube's filters. This video was taken down, and the whole channel got caught up in the algorithm's wrath. The channel was eventually restored, but the entire situation caused me to reevaluate my preconceived notion that everything on the internet was forever. At that point, I realized that if someone misses a piece of content that disappears (either due to takedown requests or the creator closing their own account), then it's gone forever.

This is, of course, the part of the story where I go slightly off the deep end (mostly on account of the timeframe being Black Friday/Cyber Monday weekend), and buy a [Synology NAS](https://www.synology.com/en-us/products/DS1517+) and 4x4TB HDD. My newfound purpose: to become an archive for all My Little Pony G4 fan content. I'm still in the process of catching up on the past seven years of fan works that have been produced, and I'm sure that I will be for quite a while, but as I catch up with each content creator, I create scripts to help automate the process.

If you've been reading this far, I think it's safe to assume that you are at least a little bit interested in starting a personal archive. 

### How to Archive Everything
First off, a brief disclaimer: I don't support piracy of the hard work that people have put into various fandom creations, this is purely for archival purposes to keep a vault of fandom works safe and sound in the event that they disappear from youtube or other video services. Please support creators where you can.

So with that out of the way, here's how to do begin.

#### YouTube and other audio/video services
If you want to save videos, [youtube-dl](https://github.com/rg3/youtube-dl) is the command line application to do it. It's fast, highly configurable, and it's easy to add it to any automation pipeline. I recommend reading through all of the different options to find what best fits your needs. If you don't care about format, and just want to download videos with the default options, it's as simple as: `youtube-dl [url]`, or `youtube-dl -o "%(uploader)s/%(title)s.%(ext)s" [url]` to set an output format using python string formatting. For the second option, I recommend reading the readme file to see all of the formatting options. These are good if you want the best quality, regardless of format, but if you care about specific formats (like I do) then you might want to pick up [ffmpeg](https://www.ffmpeg.org/download.html), a video encoder, decoder, transcoder, and so much more. You can download alternate formats without ffmpeg, but if you want to merge them together into a specific format, then ffmpeg will do it for you automatically. All you need to do is specify the formats to download and the container format that they should be merged into by using the `-f` flag, like so: 

    -f 'bestvideo[ext=mp4]+bestaudio[ext=m4a]/mp4'

This would download the best available mp4 video and best available m4a audio, and then ffmpeg will merge them into an mp4 container. There are many other options that I encourage you to look over, including filtering, playlist ordering, and meta data downloading. And don't be fooled, even though the program is named "youtube-dl," it supports a wide variety of video hosts, and even SoundCloud! This can take care of a large amount of fan works due to the number of services that youtube-dl supports.

#### Tumblr
Tumblr is one of the more irritating things to backup, and as more and more artists put all of their media on a tumblr (especially fan blogs for specific characters of a series), it becomes a greater priority to back up all of the different types of media contained within one. [tumblr-utils](https://github.com/bbolli/tumblr-utils) is the project that will help you with this task. Specifically, you will want to use the `tumblr_backup.py` script.

It works very similar to youtube-dl in that you can just feed it something to backup as an argument and let it run, like this: `./tumblr_backup.py [blog-name]` (note, this is just the part of the url that precedes the `.tumblr.com` part of the url. This will save all of the media and posts, creating an HTML document that will let you browse them in whichever order you specify *at the time that you download the blog* (and yes, that means that if you don't want it ordered in reverse, you might want to test it on a small blog before you begin mass archiving). If you have youtube-dl installed, (and if you don't have the same issues that I had on a Mac), then you should be able to use the flags `--save-audio` and `--save-video` to save posts of those types (note, tumblr_backup will use whatever your default settings are for youtube-dl, so that could mean that you end up with webm files when you want mp4. You will have to futz with the downloaded files if you want to change them after the fact). There is also an incremental backup mode which is good for blogs that are still ongoing. When using the `-i` flag, only posts that have higher ids than the highest id saved locally.

#### Images
Images are tricky. They are everywhere, and often uploaded to multiple services. There isn't one easy solution to this, but searching GitHub for projects with the name of the image hosting service that you're interested in is a good place to start. Alternatively, if you aren't interested in mass downloading, then you can usually just download the full size version of each image that you come across. Speaking with some of my friends, I can tell you that deviantArt's API does not work well all of the time, and if you are looking for a more reliable way of tracking uploads, you might want to look into a good RSS reader.

Ultimately there is no easy answer for images, and you will have to do some work yourself to find a good mass-downloader if you need one, otherwise, saving images as you come across them should be sufficient.

### In other news
It has been an incredibly long time since I have posted anything, and I think I just need to accept that will be my *modus operandi* for the foreseeable future. The time was not wasted, however: I have been making good on my previous post and am in the process of finishing up a C++ based WIN32 application (for academic and practical purposes), and I plan on releasing it sometime in the near future.

Also, that D&D campaign has been going well, albeit rather slowly, but that's due to scheduling conflicts more than anything.

Finally, *a Merry Christmas too you all!*