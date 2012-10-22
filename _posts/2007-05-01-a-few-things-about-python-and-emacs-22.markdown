--- 
wordpress_id: 84
layout: post
title: A Few Things About Python and Emacs 22
date: 2007-05-01 23:55:23 -07:00
wordpress_url: http://hupp.org/adam/weblog/2007/05/01/a-few-things-about-python-and-emacs-22/
---
This  week I upgraded to the not-quite-released emacs 22.  One of the big changes (for me at least) is the new default implementation of the python major mode, python.el.   Some observations:


 1. python.el does not seem to have the same kinds of problems with syntax highlighting of triple-quoted strings that python-mode did.   This alone is worth the upgrade in my mind.  

 1. In python-mode.el the RET key was bound to py-newline-and-indent.  When you typed 'if condition:RET' this would automatically indent the next line within the 'if' block.  In python.el this functionality is bound to "C-j" instead of RET.  You can get the old behavior (which I prefer) by putting this in your .emacs:

    <pre><code>
    (add-hook 'python-mode-hook
              (lambda ()
                (define-key python-mode-map "\C-m" 'newline-and-indent)))
    </code></pre>

    <i>Thanks to [johan](http://hupp.org/adam/weblog/2007/05/01/a-few-things-about-python-and-emacs-22/#comment-5) for the suggestion to do this in a hook.</i>

 1. Turn on [transient-mark-mode](http://www.emacsblog.org/2007/02/20/newbie-tip-transient-mark-mode/).  This is necessary for certain features like region (un)comment region (M-;) to work.  In emacs 21 transient-mark-mode didn't play well with python-mode, (e.g.  py-mark-block didn't work) so I turned it off.  That doesn't seem to be a problem anymore.


I'm sure there are many more changes but those are what I've noticed after bit of use.  Overall I'm happy with the new implementation.  
 
My next task will be to get Guido's [xreload](http://mail.python.org/pipermail/edu-sig/2007-February/007787.html) to work from  emacs.  
