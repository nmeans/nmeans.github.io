---
layout: post 
title: The Magic of top
category: links
---
After receiving several replies to a random [gripe](http://twitter.com/nmeans/statuses/967509789) I aired via Twitter, I’ve realized I’m not the only one frustrated by the differences between Linux-flavored and BSD-flavored top. Like a lot of people, I do my dev work on a Mac but deploy to a Linux production environment, so I’m constantly switching between Linux and BSD top (OS X is based on [BSD](http://en.wikipedia.org/wiki/Berkeley_Software_Distribution), not Linux.)

### What is ‘top’, anyway?

If you’ve used Windows Task Manager or OS X’s Activity Monitor, you’re already familiar with what `top` does. `top` is basically the *nix command line version of those two programs. It’s your one-stop-shop for any information you need on how loaded your system is and what specific processes are eating all that RAM or CPU time, but a little knowledge on how to use it goes a long way.

### Linux-style ‘top’

Despite using OS X on a day-to-day basis, I’m far more familiar with Linux’s `top` command. It’s got a lot more functionality than BSD’s `top`. Here’s the basics:

#### Right After You Launch

The first things I do after launching top on Linux are press ‘z’ to turn on color and then ‘x’ to turn on sort-field highlighting. There’s no command line flags to do this for you, but I’ll explain a bit later how to save this as your default configuration.

#### Sorting

There’s several ways to sort your process list in Linux’s `top`. Most of the time you’ll want to sort by Memory Percent Usage or CPU Percent Usage, and thankfully Linux provides us handy shortcuts for this (yes, they’re all uppercase - just type them in the main `top` screen):

* `M` - Percent memory usage
* `P` - Percent CPU usage
* `N` - PID
* `T` - Execution time

If you want to sort by a field other than those four, there are two ways to do it. First, you can use ‘<' or '>‘ to cycle through the sort columns. (This really isn’t useful unless you’ve typed ‘x’ first to turn on sort-field highlighting, though - how would you know what you were sorting by?) You can also type ‘O’ or ‘F’ to pick your sort column from a list.

Finally, if for some odd reason you need to know what programs on your system are using the least CPU or memory, you can type ‘R’ to reverse the sort order on the current field.

#### Interacting with Tasks

There’s plenty of other stuff you can do in Linux’s `top`, but the only other function I find useful on a regular basis is killing/renicing runaway tasks. To kill a task, type ‘k’ and enter the task’s PID. top will ask you what type of signal to send, the default being ‘SIGTERM’ (probably what you want, but if a process just won’t die, ‘KILL’ can be useful here as well). You can also renice a process by typing ‘r’. A negative number will give the process more priority, and a positive number less.

#### Default Configuration

If you get tired of typing ‘z’, ‘x’, ‘P’ as soon as you launch to get your color and favorite sort order, then the ‘W’ command is your friend. Once you get your top just like you like it, type ‘W’ and top will write out a configuration file to ~/.toprc and your top will launch with that set of parameters every time.

### BSD-style ‘top’

Thanks to my reliance on OS X’s Activity Monitor, my BSD top-fu is weak, but writing is an exercise in learning.

#### Sorting

There’s no quickie shortcuts to sorting BSD’s `top`, but thankfully there is interactive sorting available. To use it, type ‘o’ and `top` will ask you for a sort field. You can also type ‘O’ and top will ask you for a secondary sort field. Here’s an abbreviated list of sort keys - check the man page for more:

* `command` - Command name
* `cpu` - CPU usage
* `rsize` - Resident memory size
* `time` - Execution time
* `vsize` - Total memory size

You can also specify sort order on the command line using the ‘-o’ and ‘-O’ flags just like you would use them interactively. Eg.: `top -o cpu -O rsize`

#### Interacting with Tasks

BSD’s top also gives us a way to send signals to a given process. Type ‘S’ and top will ask you what signal to send, defaulting to ‘TERM’ (which is probably what you want - again, use ‘KILL’ for stubborn tasks). After setting your signal, top will ask you for the PID to send the signal to. One thing to remember is that, if you use a signal other than the default, top will default to that signal the next time you invoke the ‘S’ command.

### Wrapping Up

There’s quite a bit more tweaking possible with top than what I’ve explained here. The best source of info, like all *nix commands, is the man page for top on each operating system.