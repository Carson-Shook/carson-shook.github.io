---
layout: post
title: Cursed-breakout Update v0.5 alpha
published: true
---
Well, it's been a little while since I've released an update for this game, but I assure you that I was working hard (almost) the entire time. This update actually makes it a real game with a fail state, a score, and assorted nice things. I'm not quite ready to move to beta status yet, since it's fixed to a single level with no pausing and no speed increase or way to keep going afterward.

If you want to download, just click the following link, or visit the project directly on GitHub. To build, just type `make` in the terminal, and run the game with `./breakout`

[Download cursed-breakout v0.5a](https://github.com/Carson-Shook/cursed-breakout/archive/master.zip)

The next update should include at the very least a single *repeating* level, or more hopefully support for a series of custom designed levels stored in a text file in the same directory. You should also be able to look forward to the ability for the ball to change X and Y velocity when it hits the paddle. It will naturally come with minor adjustments to the design of the score board, and possibly some preparations for a power-up system (here's hoping).

That's all for now. The changelog from this update is below, and if you want the complete changelog, please visit the project [directly on GitHub](github.com/Carson-Shook/cursed-breakout).

### Changelog
- Added ball reset, life count, and **Game Over** screen
- Added score system with multiplier for each successful hit
- Added up and down arrow key condition checks to allow for moving the paddle twice as fast
- Moved collision system into `main`
- Fixed a bug with the lower right corner of the ball (the case was being skipped on accident)
- Fixed a slight error in my math that sometimes caused problems for bricks that were on the right side of the game screen
- Fixed slowdown caused by debug mode
- Updated Makefile to include the C math library to perform a logarithmic function in the program.