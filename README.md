dpkg-purge-deleted
==================

Removes all deleted but not purged packages on Debian and Ubuntu
systems.

Rationale
---------

When you remove packages via _dpkg_, _apt-get_ or _aptitude_, it
doesn't remove everything, it leaves things like configuration files
behind. You can tell each of these commands to delete those as well
(i.e. purge), but I sometimes forget. Plus _apt-get autoremove_ can't
do it.

In the past few years, I regularly did something like this:

    for i in `dpkg -l | grep ^rc | cut -d" " -f 3`; do dpkg -P $i; done

But today I was fed up with that. Today I created this script.

Installation
------------

[Download the script](https://raw.github.com/fhd/smvn/master/smvn),
put in on root's `$PATH` and make it executable.

Usage
-----

Just execute `dpkg-purge-deleted` as root. Don't worry, it will ask
you before purging anything.
