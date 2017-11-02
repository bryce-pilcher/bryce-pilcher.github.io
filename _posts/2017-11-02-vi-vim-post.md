---
layout: post
title: "On vi and Vim"
date: 2017-11-02
category: blog
---

For some strange reason I love working with documents and code in Vim. To a
beginner the controls can certainly seem unintuitive, but I loved it anyways.
Perhaps because it took me back to my undergrad days when programming was
simple and the methods were all so new and exciting.  

When I was an undergrad at NCSU the first CSC (Computer Science) class I took
was CSC 116 Intro to Java. In that class we used a Linux machine and programmed
in the terminal exclusively. We were not introduced to the joys of IDE's until
much later.  Back to that first class, as part of the introduction we were told
about the various editors: pico, nano, gedit, etc.  There was one they did not
recommend because it was a challenge to use, so naturally I had to learn Vim.

They warned there was no mouse support and thus all the navigation was done on
the keyboard.  This lent itself to two modes; a command mode and an insert
mode. One has to be careful because in command mode all those keys one uses to
insert text become commands to navigate, delete, etc.

I knew the basics of Vim. `i` puts Vim in insert mode and you mash `esc` to
jump out of insert and punch `:wq` followed by `enter` to quit Vim.  The arrow
keys provided navigation throughout the text in the file. This was a real pain
if the file contained extremely long lines of text.  Thus is really taught me to
keep my lines short and concise in my programs. In command mode you could enter a line
number followed by `G` to go to a line; i.e. `70G`. Also in command mode you
could search for text using `/` followed by the search term and iterate through
each instance by presssing `n`.  That was about all I knew, and it was enough
for me to love my experience with Vim. 

I picked up an excellent book from one of [Humble
Bundle's](https://www.humblebundle.com/books){:target="_blank"} book bundles, [*Learning the vi and
Vim
Editors*](http://shop.oreilly.com/product/9780596529833.do){:target="_blank"}.  In woking through just the first three chapters my understanding
of Vim has gone from elementary to amatuer.  By no means am I anywhere near
advanced or mastery, but I am certainly quite a ways forward in navigating and
working on documents. The commands are actually intuitive, they just require
practice to recall and use properly.

I will be creating a cheatsheet in a separate blog post and will link to that
one here.  I hope you enjoy using the cheatsheet as much as I do, because it
truly makes Vim a more freeing and powerful tool.
