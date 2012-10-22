--- 
wordpress_id: 5
layout: post
title: "Creating a custom search engine from RSS feeds "
date: 2007-03-26 22:57:37 -07:00
wordpress_url: http://hupp.org/adam/weblog/2007/03/26/custom-search-from-feed/
---
<b>Update:</b>The CSE team has <a href="http://googlecustomsearch.blogspot.com/2007/06/custom-search-engine-apis.html">included this functionality directly into Coop-search,</a>  so this code isn't necessary anymore.

I've been playing around with the Google <a href="http://google.com/coop/cse/">Custom Search Engine</a> (CSE) feature recently.    CSE  lets anyone create a search engine that indexes a user-defined set of URL patterns.        I thought it would useful to create a CSE based on links in RSS feeds.  The motivating example was <a href="http://programming.reddit.com">programming.reddit.com</a>.   Pages linked there are submitted and voted on by the users, and the top-ranked items are consistently interesting and relevent.  A CSE derived from sites like this is useful for a few reasons:
<ol>
	<li>Answering the question, "What was that page I saw on reddit 2 weeks ago about that thing?"  I'm often trying to track down a page I remember seeing on reddit a long time ago, and a standard web search isn't useful in this case.</li>
	<li>Building search engines that take advantage of the filtering done by human editors.  CSE can search a set of URL patterns exclusively, or can augment a full web search by emphasizing selected URLs.</li>
</ol>
I've written a set of python scripts that can turn an RSS feed into a CSE annotations file and then upload the annotation list automatically.      Here is an example of <a href="http://hupp.org/adam/reddit-cse/">the resulting search engine</a>.    At the time of writing this CSE searches 1,323 web pages collected from the programming.reddit.com RSS feed over the last month.  The set of links is updated once a day by a cron job.

More information on how to run the scripts yourself is in the <a href="http://hupp.org/adam/svn/public/feedcse/trunk/README">README</a> file.  The code is distributed under the <a href="http://www.python.org/psf/license/">PSF licence</a> and can be retrieved with a subversion client <a href="http://hupp.org/adam/svn/public/feedcse/trunk">from here</a>.  Any feedback is of course appreciated.

Note: According to my reading of the CSE <a href="http://www.google.com/coop/docs/cse/tos.html">TOS</a> this is a legitimate usage.  I  asked on the <a href="http://groups.google.com/group/google-co-op">group</a> and had no response.  If anyone knows otherwise please let me know.
