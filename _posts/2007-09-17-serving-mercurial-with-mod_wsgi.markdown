--- 
wordpress_id: 99
layout: post
title: Serving mercurial with mod_wsgi
date: 2007-09-17 23:39:36 -07:00
wordpress_url: http://hupp.org/adam/weblog/2007/09/17/serving-mercurial-with-mod_wsgi/
---
Here's a quick and easy recipe for serving a [mercurial](http://www.selenic.com/mercurial/) repository with [mod_wsgi](http://modwsgi.googlecode.com/).  

 1. Create a file called hgwebdir.wsgi with these contents:

        from mercurial.hgweb.request import wsgiapplication
        from mercurial.hgweb.hgwebdir_mod import hgwebdir

        def make_web_app():
            return hgwebdir("/path/to/hgweb.config")

        application = wsgiapplication(make_web_app)
    
 2. Add it to the apache configuration:

   WSGIScriptAlias /hg /path/to/hgwebdir.wsgi

 3. [optional] To make sure nobody modifies your repository via the http interface, add 'deny_push = *' to the '[web]' group of hgweb.config.

Hopefully this page will save the next person a few minutes of searching.
