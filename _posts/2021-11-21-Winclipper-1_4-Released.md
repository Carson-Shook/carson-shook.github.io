---
layout: post
title: Winclipper 1.4 Released
published: true
comments: true
---
**Update:** I had to push out 1.4.1 real quick to fix an issue with the updater continuously popping up on startup. Sorry for the inconvenience!

This release of Winclipper includes the following features and bug fixes:
- Dark Mode! Winclipper now follows your window color settings in Windows 10 and up in the Settings menu. I might expand this in the future.
- Adds an option for "Paste immediately on click" that can be disabled so that Winclipper only adds items to the clipboard, but still lets the user do the pasting.
- Added one-time startup message to alert users if they have Windows Clipboard History turned on as it can interfere with Winclipper.
- Lots of safety refactoring to try and clean up any remaining memory issues and crashes. If you get an alert that a fatal error has occurred, please report it at [https://github.com/Carson-Shook/Winclipper/issues](https://github.com/Carson-Shook/Winclipper/issues)