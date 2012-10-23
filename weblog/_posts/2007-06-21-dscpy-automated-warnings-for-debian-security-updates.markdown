--- 
wordpress_id: 92
layout: post
title: "dsc.py: Automated Warnings for Debian Security Updates"
date: 2007-06-21 03:00:33 -07:00
---

[dsc.py](https://github.com/ahupp/debian-security-check) (Debian
Security Check) is a Python script that automatically notifies a
machine's administrator when installed packages require a security
upgrade.

### Why this is useful

This week there were 9 Debian security advisories released, and I
don't always know which ones apply to my server.  This is especially
hard in the case of libraries (think fast: do any of your services
depend on [freetype](http://www.debian.org/security/2007/dsa-1302)?).
dsc.py will only notify you of packages that actually require
upgrades.

The alternative is to put an 'apt-get upgrade' directly in crontab,
but I'd prefer to do upgrades by hand.

### How does it work?

Necessary upgrades are determined by comparing the packages listed in
the [security advisories RSS
feed](http://www.debian.org/security/dsa-long) with the set of
upgradeable packages.  When a match is found a summary of the issue is
written to stdout.  This script is run via cron nightly, with output
(if any) mailed to the administrator.  Note that an 'apt-get update'
will need to be run first.  My crontab entry looks like this:

    0 3 * * * apt-get -qq update && /usr/local/bin/dsc.py

dsc.py depends on these packages: python, python-apt, dctrl-tools, and
python-feedparser

[It can be downloaded from github](https://github.com/ahupp/debian-security-check)
