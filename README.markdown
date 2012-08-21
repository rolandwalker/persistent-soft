Overview
========
Persistent storage for Emacs, returning nil on failure.

persistent-soft
---------------
This is a (trivial) wrapper around pcache.el, providing "soft"
fetch and store routines which never throw an error, but instead
return nil on failure.

There is no end-user interface for this library.  It is only
useful from other Lisp code.

The following functions are provided

	persistent-soft-exists-p
	persistent-soft-fetch
	persistent-soft-flush
	persistent-soft-store

To use persistent-soft, place the persistent-soft.el library
somewhere Emacs can find it, and add the following to your
~/.emacs file:

	(require 'persistent-soft)

See Also
--------
M-x customize-group RET persistent-soft RET

Notes
-----
Using pcache with a more recent version of CEDET gives

	Unsafe call to `eieio-persistent-read'.
	eieio-persistent-read: Wrong type argument: class-p, nil

This library provides something of a workaround.

Compatibility
-------------
Tested only on GNU Emacs version 24.x

Bugs
----
Persistent-soft is a wrapper around pcache which is a wrapper
around eieio.  Therefore, persistent-soft should probably be
rewritten to use eieio directly or recast as a patch to pcache.
