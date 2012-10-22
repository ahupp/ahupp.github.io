--- 
wordpress_id: 103
layout: post
title: Burkhard-Keller (BK) Trees In Python
date: 2007-10-28 19:02:28 -07:00
wordpress_url: http://hupp.org/adam/weblog/2007/10/28/burkhard-keller-bk-trees-in-python/
---
I recently came across a [description of an interesting data structure](http://blog.notdot.net/archives/30-Damn-Cool-Algorithms,-Part-1-BK-Trees.html) called a Burkhard-Keller tree (BK tree).   BK trees provide efficient lookup of the set of words that lie within a certain distance of a query word.   For example, this could used to suggest corrections in a spell checker.

To play around with this I've written up a Python implementation of the tree.  For example:

    >>> tree = BKTree(levenshtein, dictionary_words)
    >>> tree.query("ricohet", 2)
    [(1, 'ricochet'), (2, 'richer'), (2, 'riches'), 
     (2, 'richest'), (2, 'ricochets')]
    >>>

In the above example 'levenshtein' is a function that implements the [Levenshtein Distance](http://en.wikipedia.org/wiki/Levenshtein_Distance).  This is commonly used to determine the distance between a word and its misspellings.

How much faster is a bk-tree than the brute force approach?  Here are a few example queries compared with the brute-force time:

<table border="1">
<tr><td>word, distance</td><td>BK Tree</td><td>Brute Force</td></tr>
<tr><td>amphibious, 2</td><td>3s</td><td>15s</td></tr>
<tr><td>ricochet, 2</td><td>3s</td><td>11s</td></tr>
<tr><td>the, 2</td><td>0.2s</td><td>6s</td></tr>
</table>

You can see the BK tree is much faster for small distances.  As the query distance increases the BK tree query time approaches that of the brute force method.

Of course, there's no free lunch.  Creating this tree of 57,024 words takes 94s on my system.

The source for this module [is available here](http://hupp.org/adam/hg/bktree/file/tip/bktree.py).  Enjoy!
