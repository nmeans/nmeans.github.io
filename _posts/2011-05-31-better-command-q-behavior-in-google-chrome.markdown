---
layout: post
title: Better ⌘Q Behavior in Google Chrome 
category: posts
---
With Q and W being right next to each other on the QWERTY keyboard, it's much too easy to hit ⌘Q when you really meant to just close the window with ⌘W. Most applications deal with this gracefully by asking you if you really want to quit, but Google Chrome is not among them.

Accidentally hit ⌘Q and you're stuck re-opening Chrome and picking "Re-open All Recently Closed Tabs" under the history menu. It works, and you don't lose anything, but it can take quite some time to re-load all of this when you have 20 tabs open (as I often do).

If you're a Mac user, you're in luck! The (unfortunately Mac-only) fix is to type '`about:flags`' in the address bar to open Chrome's hidden configuration page. About half-way down the page, there's an item called "Confirm to Quit". Enable that, and you're good to go. Chrome will now be a good citizen and ask if you really meant to quit.

**Update:** This has graduated from '`about:flags`' to a real option in Chrome 12, but instead of being in the prefs, it's oddly placed in the 'Chrome' menu. Just select 'Chrome' > 'Warn Before Quitting' and you're good to go!