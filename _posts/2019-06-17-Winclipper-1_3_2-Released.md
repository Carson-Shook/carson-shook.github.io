---
layout: post
title: Winclipper 1.3.2 Released
published: true
comments: true
---
I forgot to make a post for version 1.3.1, but to summarize, I fixed an issue with duplication of bitmaps and made sure that bitmaps were prioritized over text for previews. Now that that's out of the way, lets move on to the 1.3.2 patch notes:

- Fixed a race condition that caused a build-up of orphaned bitmaps on disk. If you want to clean up any existing orphaned bitmaps, I recommend unchecking "Save clips to disk" in the Settings window, waiting at least 5 seconds (or a little longer for non-SSDs), and then checking the box again. Those who did not use this setting in the first place were not affected. Unfortunately this fix might lead to a slight loss in performance when copying large amounts of data quickly.
- Fixed a counter that was not correctly implemented that would cause a resource leak when a large bitmap failed to preview in 5 seconds.
- Added a check that prevents copying images larger than 16384 pixels in either direction because they break the Windows Imaging Component, thus breaking the preview window and causing a resource leak.
- Added a fix for non-device independent bitmaps that do not correctly handle alpha channel information. Now your bitmaps copied from Excel should actually appear in the preview!
    - Technical explanation for those who need it: if a 32-bit bitmap is of type CF_BITMAP rather than CF_DIB, then all alpha channel bytes are set to 255 since Winclipper handles all bitmaps internally as CF_DIB and otherwise cannot make the distinction about whether or not to use transparency.

Also I watched *Godzilla: King of Monsters* today (which would be Saturday, however this post will be going live on Monday so these events have taken place in the past by the time that you read this), and someone scraped my car in the parking lot of the theater, but they were nice enough to leave their number. The movie was pretty good, though it could have used a little bit more monster fighting. 7.2/10

Anyway, if no more bugs pop up, then you can officially consider my work on Winclipper to be finished until further notice. Thanks for everyone who supported me in building this little project and for those who gave me valuable feedback! You're the best! 👍