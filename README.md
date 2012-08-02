repo-push
=========

Mercurial extension that suffixes any path name with “-push” for outbound operations.

Status
------

**This extension is not distributed with Mercurial.**

Author: Daniel Rodríguez Troitiño

Repository: https://github.com/drodriguez/repo-push.git

Web page: https://github.com/drodriguez/repo-push

Overview
--------

If you run `hg help paths` in recent versions of Mercurial, one of the last paragraphs tells you the following:

    The path names "default" and "default-push" have a special meaning.  When
    performing a push or pull operation, they are used as fallbacks if no
    location is specified on the command-line. When "default-push" is set, it
    will be used for push and "default" will be used for pull; otherwise
    "default" is used as the fallback for both. [...] Note that "default" and
    "default-push" apply to all inbound (e.g. "hg incoming") and outbound (e.g.
    "hg outgoing", "hg email" and "hg bundle") operations.

Amazingly that special suffix only works with *default* and not with any other
path you may create.

This extension enables the use of the special suffix “-push” for any path set
in your Mercurial config. You just need to create the pair “myrepo” and
“myrepo-push” and the extension will take care of using “myrepo-push” for the
outbound operations (currently this operations are `push`, `outgoing` and
`bundle`). If no “-push” suffixed version is found, the provided path will be
used.

Configuration
-------------

Download repo-push.py somewhere in your computer. Configure your `.hgrc` to enable the extension by adding following lines:

    [extensions]
    repo-push = /path/to/your/repo-push.py

Then you can just create a repository pair in your `.hg/hgrc` file:

    [paths]
	default = http://example.com/default/pull
	default-push = http://example.com/default/push
	alternate = http://example.com/alternate/pull
	alternate-push = http://example.com/alternate/push
