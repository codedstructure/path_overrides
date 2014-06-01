Path Overrides
==============

Detects executables which 'override' other executables in the system PATH.

Use
---

Run `path_overrides`. It will display a list of which executables shadow other (different) executables.

Motivation
----------

If I press the 'tab' key a couple of times on a recent Linux or OS X shell, I get a prompt looking something like::

    Display all 2228 possibilities? (y or n)

There are over 2000 commands all ready and waiting to be run at a single word being entered. And these don't all live in one place; they live in a (typically small) number of different locations, which are listed in the `PATH` environment variable. `PATH` is an ordered sequence of paths which are searched to find an executable which will be run. This works well for the most part, but as with all things where there isn't a single namespace, collisions happen. There could be a number of items all with the same name living in different paths all in `PATH`. In normal use this isn't a problem; `PATH` is ordered, and each part of it is a unique no-collisions-possible directory. There is never non-determinism about which executable will 'win', and the `which` shell program will report on 'which' path has precedence.

However, unless you are in the habit of regularly running `which` before executing any command - or only ever run commands with absolute pathnames - there can be surprises; if someone places a executable earlier in the `PATH` than the one you would expect to be run, it will take precendence. `path_overrides` will report on any command which overrides a *different* command later in the `PATH`. Note it's quite common to have symlinks from (e.g.) `/usr/bin` to programs in `/bin`; since they represent 'the same command', `path_overrides` will ignore these.

@codedstructure 2014
