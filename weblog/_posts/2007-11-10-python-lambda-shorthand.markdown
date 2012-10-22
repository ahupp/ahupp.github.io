--- 
wordpress_id: 106
layout: post
title: "Python λ Shorthand"
date: 2007-11-10 15:55:45 -08:00
wordpress_url: http://hupp.org/adam/weblog/2007/11/10/python-%ce%bb-shorthand/
---
In Python a lambda expression (anonymous function) is created with the `lambda` keyword:

    map(lambda x: x+1, [1,2,3])

Some Scheme interpreters such as
[Dr. Scheme](http://www.plt-scheme.org/software/drscheme/) allow the λ
symbol
([U+03BB](http://www.fileformat.info/info/unicode/char/03bb/index.htm))
as a shorthand for lambda.  I started wondering what this would look
like in Python.  For example:

    map(λ x: x+1, [1,2,3])

There are a few cases where the shorthand is beneficial.  For example, compare:

    [i for i in lst if i > 42]

to:

    filter(λ x: x > 42, lst)

While list comprehensions are the standard python way to accomplish
this, I really prefer how the predicate comes first in the latter
version.  Most of the functions in the itertools module could work
nicely with the shorthand form:

    itertools.groupby(lst, λ x: x.somevalue)

For a slightly more gratuitously complex example, a recursive
factorial with the Y combinator:

    Y = (λ X:
             (λ p:
                  X(λ arg: p(p)(arg)))
         ((λ p:
               X(λ arg: p(p)(arg)))))

    F = (λ f: (λ x: (x*f(x-1) if x > 0 else 1)))

    fact = Y(F)
    fact(5) => 120

*Update*: This post used to contain an interpreter patch that defines
λ as a synonym for lambda , but a much simpler solution is to do the
transformation at display time in emacs.  That setup is [described
here](http://www.emacswiki.org/emacs/PrettyLambda).

