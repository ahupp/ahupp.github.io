--- 
wordpress_id: 98
layout: post
title: "etframes: Applying the ideas of Edward Tufte to matplotlib"
date: 2007-09-03 22:01:29 -07:00
wordpress_url: http://hupp.org/adam/weblog/2007/09/03/etframes-applying-the-ideas-of-edward-tufte-to-matplotlib/
---
[Edward Tufte](http://en.wikipedia.org/wiki/Edward_tufte) is a professor and author known for his excellent (and beautiful!) books on the visual display of statistical information.  Last year I had the opportunity to attend one of his [courses](http://www.edwardtufte.com/tufte/courses) and was inspired to apply his ideas to my favorite plotting library, [matplotlib](http://matplotlib.sourceforge.net/).   

The result is [etfames](http://hupp.org/adam/svn/public/etframes), a python module that operates on matplotlib plots.  So far I've implemented two graph types described in the [The Visual Display of Quantitative Information (VDQI)](http://www.amazon.com/gp/redirect.html?ie=UTF8&location=http%3A%2F%2Fwww.amazon.com%2FVisual-Display-Quantitative-Information-2nd%2Fdp%2F0961392142%3Fie%3DUTF8%26s%3Dbooks%26qid%3D1188758757%26sr%3D8-1&tag=rococothenrub-20&linkCode=ur2&camp=1789&creative=9325):  the dash-dot-plot and range frames.

Dash Dot Plot
-------------

A dash-dot-plot places a tick mark on the axis for each value in a scatter plot.  When there are many values in the graph this can be a more effective way to understand their distribution than looking at the raw data.  For example:

<a href="/adam/images/ddp.png">
<img alt="Example of a dash-dot-plot" src="/adam/images/ddp.png"/></a>

See [demo_ddp.py](http://hupp.org/adam/svn/public/etframes/demo_ddp.py) for a working example.

Range Frames
-------------

The range frame re-uses the frame (edge) of a graph to display useful information.  Instead of drawing a full frame around the graph the frame is only drawn from the minimum to the maximum value along that axis.  For example:

<a href="/adam/images/range.png">
<img alt="Example of a range frame" src="/adam/images/range.png"/></a>

See [demo_range.py](http://hupp.org/adam/svn/public/etframes/demo_range.py) for a working example.

Other Work
------------

There are several other graph types described in VDQI that would be nice to implement, particularly the extension of range frames that turns them into a [box plot](http://en.wikipedia.org/wiki/Box_plot).

A related project is [sparkplot](http://sparkplot.org/) which uses the matplotlib library to create sparklines.
