--- 
wordpress_id: 106
layout: post
title: "Python \xC3\x8E\xC2\xBB Shorthand"
date: 2007-11-10 15:55:45 -08:00
wordpress_url: http://hupp.org/adam/weblog/2007/11/10/python-%ce%bb-shorthand/
---
In Python a lambda expression (anonymous function) is created with the `lambda` keyword:

    map(lambda x: x+1, [1,2,3])

Some Scheme interpreters such as  [Dr. Scheme](http://www.plt-scheme.org/software/drscheme/) allow the Î» symbol ([U+03BB](http://www.fileformat.info/info/unicode/char/03bb/index.htm)) as a shorthand for lambda.   I started wondering what this would look like in Python.  For example:

    map(Î» x: x+1, [1,2,3])

Or for a slightly more gratuitously complex example, a recursive factorial with the Y
combinator:

    Y = (Î» X:
             (Î» p:
                  X(Î» arg: p(p)(arg)))
         ((Î» p:
               X(Î» arg: p(p)(arg)))))

    F = (Î» f: (Î» x: (x*f(x-1) if x > 0 else 1)))

    fact = Y(F)
    fact(5) => 120

The interpreter changes to make this work this are quite simple.  All it requires is small change to the grammar, an update to the syntax checker, and a hack in the parser generator to treat characters with the high-bit set as though they were in the alpha class.

There are a few cases where the shorthand is beneficial.  For example, compare:

    [i for i in lst if i > 42]

to:

    filter(Î» x: x > 42, lst)

While list comprehensions are the standard python way to accomplish this, I do like how the predicate comes first in the latter version.  

Also, pretty much all of the functions in the itertools module could work nicely with the  shorthand form:

    itertools.groupby(lst, Î» x: x.somevalue)


Even so this is probably isn't something that would be worth adding to the language.
Lambda expressions are rarely useful in Python so a shorthand form is not going at add much benefit compared to the added language complexity.  Not to mention the need for a UTF-8 aware editor and terminal.  


Using It
-------

Since Î» probably doesn't appear on your keyboard a certain amount of editor configuration is required.  The easiest way in emacs is to define a key binding that inserts the character:

    (global-set-key "\C-c\C-l" (lambda () (interactive) (insert "Î»")) )

Alternatively, abbrev-mode can insert this character whenever the word `lambda` is typed:

    (define-abbrev-table 'global-abbrev-table
      '(("lambda" "Î»" nil 0)))


To build an interpreter with this enabled you'll need [this patch](/adam/python-lambda-shorthand.patch) applied to a recentish checkout of python 3k.  I don't know if it would work on earlier versions. 

**Update:**  On reddit, [gwern pointed out](http://programming.reddit.com/info/60bo6/comments/c02g6ee) that it's better to translate from lambda -> Î» in the editor display rather than embed this symbol in the text.  There is (of course) [elisp to do this](http://www.emacswiki.org/cgi-bin/wiki/PrettyLambda).
