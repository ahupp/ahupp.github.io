--- 
wordpress_id: 80
layout: post
title: Code Critique as an Interview Tool
date: 2007-04-15 22:21:36 -07:00
wordpress_url: http://hupp.org/adam/weblog/2007/04/15/code-critique-as-an-interview-tool/
---
One of a software engineer's most critical skills is the ability to
**read** code.  In my experience developers spend far more time and
effort reading code than writing it.  Others agree ([Joel On
Software](http://www.joelonsoftware.com/articles/fog0000000069.html),
[Jeff Atwood](http://www.codinghorror.com/blog/archives/000684.html)).
It stands to reason that this is a skill that should be looked for
during the interview process.  I've found that code critiques can be a
valuable tool in this regard.

They answer questions such as: Can this person see bugs?  Can they
comprehend an unfamiliar piece of code?  Are they opinionated about
what good code should look like?

For this purpose I came up with a stack-like class that fits on a
single sheet of paper.  This class has a variety of flaws ranging from
the painfully obvious to the subtle. The candidate takes a few minutes
to look over the sheet and then we spend 10-15 minutes talking about
code.  The issues include:

 1. Poor method naming  ("*doIt*")
 1. Poor time complexity (O(n) when O(1) would do).
 1. Duplicated code
 1. Handling of error cases (does a pop on an empty stack corrupt the
    datastructure?)
 1. Memory leaks
 1. (Java-specific) Misimplemented *Object#equals* method
 1. Input validation (does pushing a null onto the stack cause later failures in the *contains* method?)
 1. Inconsistent and/or non-existent comments


What I like about this process is that it give a very fine-grained
scale to understand how someone thinks.  If they don't mention
something you can start a conversation on that topic.  "So what do you
think the time complexity of pushing N items would be?  Could it be
better?" "What happens if multiple threads use the class at once?"

So far I've tried this on a small sample of candidates and it has been
a reliable discriminator.  One person failed miserably, one person
more or less aced it, and a few more landed somewhere in the middle.
With more time and experience I hope to refine the process further.  I
would love to hear from others who have thoughts or experience with
this technique.
