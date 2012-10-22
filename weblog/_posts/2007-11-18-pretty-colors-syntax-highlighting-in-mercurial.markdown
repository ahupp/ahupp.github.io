--- 
wordpress_id: 105
layout: post
title: "Pretty colors: Syntax Highlighting in Mercurial"
date: 2007-11-18 23:43:30 -08:00
wordpress_url: http://hupp.org/adam/weblog/2007/11/18/pretty-colors-syntax-highlighting-in-mercurial/
---
I recently switched my personal revision control system from
subversion to [mercurial](http://selenic.com/mercurial).  One of the
great things about mercurial is the built-in web interface, but I
missed the syntax highlighting that's available in interfaces such as
[ViewVC](http://viewvc.org).

I've written a mercurial extension that applies
[pygments](http://pygments.org) code highlighting.  This extension is [now
available](http://www.selenic.com/repo/hg/file/tip/hgext/highlight/highlight.py)
in the main mercurial repo.

To enable it, install pygments and add the following entry to hgrc:

    [extension]
    hgext.highlight =

Thanks to *micha* who wrote an initial
[patch](http://www.selenic.com/pipermail/mercurial/2007-May/013207.html).
