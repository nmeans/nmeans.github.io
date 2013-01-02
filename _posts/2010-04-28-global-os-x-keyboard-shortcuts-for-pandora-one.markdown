---
layout: post 
title: Global OS X Keyboard Shortcuts for Pandora One
category: links
---
After much debating, I dropped the $36 to upgrade to Pandora One. I've got a big music library, but when I'm writing code I want to take breaks at natural spots, not just because an album has ended. Pandora One ups the audio quality significantly, but it also gives you access to Pandora's Adobe AIR client program. While it's a significant upgrade from in-browser Pandora, it still doesn't give you global keyboard shortcuts.

It will listen to keyboard commands when it's got focus, however, and luckily Applescript gives us a way to do that:

<script src="http://gist.github.com/382318.js?file=UniversalPlayPause.scpt"></script>

I've got that script bound to the Play/Pause key on my keyboard using the excellent [USB Overdrive](http://www.usboverdrive.com/), but if you don't have a need for Overdrive, you could use something like [Keyboard Maestro](http://www.keyboardmaestro.com/) as well. It's a bit slow on the first keypress as USB Overdrive has no way to use a pre-compiled Applescript, but it works well enough for my requirements.

I primarily listen to Pandora, so the script first checks to see if the Pandora app is running, and if so, gives Pandora focus and sends a spacebar keystroke to toggle play/pause.  If Pandora's not running, it checks for iTunes and sends the command to iTunes, so I'm not losing the normal functionality of the key. This has the nice side-effect of not launching iTunes accidentally by pressing the Play/Pause key.

You can do the same thing with the next track key if you'd like.  Pandora uses the right arrow key to skip, so we have to use the `key code` command instead of `keystroke` here:

<script src="http://gist.github.com/382318.js?file=UniversalNextTrack.scpt"></script>

There's lots more good information on sending keystrokes to apps on this page at [Doug's iTunes Scripts](http://dougscripts.com/itunes/itinfo/keycodes.php), and I got the code to check if an app is running from [a random post on Joyent's CodeSnippets](http://codesnippets.joyent.com/posts/show/1124).
