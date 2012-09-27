[![Build Status](https://secure.travis-ci.org/rolandwalker/persistent-soft.png)](http://travis-ci.org/rolandwalker/persistent-soft)

Overview
========

Persistent storage, returning nil on failure.

Quickstart
----------

```lisp
(require 'persistent-soft)
(persistent-soft-store 'hundred 100 "mydatastore")
(persistent-soft-fetch 'hundred "mydatastore")    ; 100
(persistent-soft-fetch 'thousand "mydatastore")   ; nil
 
;; quit and restart Emacs
 
(persistent-soft-fetch 'hundred "mydatastore")    ; 100
```

persistent-soft
---------------

This is a (trivial) wrapper around pcache.el, providing "soft"
fetch and store routines which never throw an error, but instead
return nil on failure.

There is no end-user interface for this library.  It is only
useful from other Lisp code.

The following functions are provided

	persistent-soft-store
	persistent-soft-fetch
	persistent-soft-exists-p
	persistent-soft-flush

To use persistent-soft, place the persistent-soft.el library
somewhere Emacs can find it, and add the following to your
~/.emacs file:

```lisp
(require 'persistent-soft)
```

See Also
--------

M-x customize-group RET persistent-soft RET

Notes
-----

Using pcache with a more recent version of CEDET gives

	Unsafe call to `eieio-persistent-read'.
	eieio-persistent-read: Wrong type argument: class-p, nil

This library provides something of a workaround.

Bugs
----

Persistent-soft is a wrapper around pcache which is a wrapper
around eieio.  Therefore, persistent-soft should probably be
rewritten to use eieio directly or recast as a patch to pcache.

Compatibility and Requirements
------------------------------

Tested on GNU Emacs versions 23.3 and 24.1

Uses if present: [pcache.el](http://github.com/sigma/pcache) (all operations are noops when
not present)
