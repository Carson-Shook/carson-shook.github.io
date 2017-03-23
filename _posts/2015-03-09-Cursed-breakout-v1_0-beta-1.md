---
layout: post
title: Cursed-Breakout v1.0 Beta 1
published: true
comments: true
---

Here it is, the big version one-point-oh beta one. I had been starting to wonder if I would ever make it this far, but evidently I'm the persistent sort. I have learned a lot of things along the way, and there are still a few things that I will likely learn before the final release. I only expect one more beta before going gold, and I suspect that I will will only include the file selector and possible level verification. But I'm getting ahead of myself.

So what can you expect in this release? **Everything!** There is now a custom level system, the ball has directional velocity, there's a pause screen (that you can access with `p`), and many more things under the hood! You can, of course, read all about these changes in the changelog down below or on its [GitHub repository](http://github.com/Carson-Shook/cursed-breakout).

If you just want to download it, just click below:

[Download cursed-breakout v1.0b1](https://github.com/Carson-Shook/cursed-breakout/archive/master.zip)

### Changelog
- Added custom level system (see example.lvl for formatting)
- Added pause screen and moved the quit option into it
- Added directional velocity for the ball. It now bounces off of the paddle at different angles depending upon where you hit it. This is accomplished with separate x and y timers, and a slew of other variables relating to the speed of the ball (or more specifically, the delay before the ball moves again)
- Moved paddle physics into the Collider
- Changed the up/down/left/right arrow keys so that left and right now move at the 2x speed, while up and down move one space at a time. I just flipped them because I found myself using up and down more often anyway.
- Changed the old method of quitting to a `quitFlag` to allow for a more intricate quit sequence
- Replaced `didUpdate` with `paddleUpdate`, `ballUpdate`, and `collisionUpdate` for more precise control over refreshes, and added `leaveok()` to reduce the need to move the curser so often
- Cleaned up calculations for better readability
- Fixed an error in my math caused by "correcting" the previous errors in the Collider
- Fixed an issue where the ball would mysteriously bounce off of the bricks backwards to how it was supposed to by adding a check to ensure that the ball was coming towards the brick first