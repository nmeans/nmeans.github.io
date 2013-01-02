---
layout: post
title: Git Tags By Date
category: posts
---
So you need to get a list of the tags in your git repository sorted by date, eh? `git tag` defaults to dumping them out sorted alphabetically, and because of the way git handles tag data, this is the only practical default. 

Git defaults to creating lightweight tags which are essentially static branches, so they have no metadata whatsoever except for a ref. If you haven't been creating annotated or signed tags (via git tag -a, -m, -s, or -u), you're actually SOL. You can't list all of your tags by date, end of story.

If you have been creating annotated or signed tags, just run the following (all on one line):

`git for-each-ref --sort='*authordate' --format='%(tag)' refs/tags`

And there you have it. Want to actually show some of the attached metadata or sort by author? Easy enough. Just check out the man page for `git-for-each-ref` and you'll have all the info you need to slice and dice your commits and tags however you'd like.

**Update:** Shad Reynolds ([@shadr](http://twitter.com/shadr)) points out on Twitter that the following:

`git for-each-ref --sort='*authordate' --format='%(refname:short)' refs/tags`

seems to show more tags than the version I posted. I did a bit of testing, and it appears that `%(tag)` only shows annotated tag names, whereas `%(refname:short)` will show lightweight tag names as well. It's a bit misleading, though. Since lightweight tags don't have the metadata needed to sort by date, they'll just show up at the top of your tag list sorted alphabetically, with all of your annotated tags below sorted by date.