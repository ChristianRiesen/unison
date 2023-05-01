![Unison](icons/unison.png)

# Unison File Synchronizer

## Meta

***Please read this entire README and
https://github.com/bcpierce00/unison/wiki/Reporting-Bugs-and-Feature-Requests
before creating or commenting on a github issue.***

***TL;DR: Do not ask questions or ask for help in issues.  Upgrade to the latest release.***

If you are trying to interoperate with or upgrade from Unison before
2.52, see the compatibility section below.  However, pre-2.52 is now
very old; see the previous paragraph.

## About

Unison is a file-synchronization tool for POSIX-compliant systems
(e.g. *BSD, GNU/Linux, macOS) and Windows, with the caveat that the
platform must be supported by OCaml.  It allows two replicas of a
collection of files and directories to be stored on different hosts
(or different disks on the same host), modified separately, and then
brought up to date by propagating the changes in each replica to the
other.

Unison has been in use for over 20 years and many people use it to
synchronize data they care about.

Unison shares a number of features with tools such as configuration
management packages (CVS, Subversion, git, Mercurial, etc.),
distributed filesystems (Coda, etc.), uni-directional mirroring
utilities (rsync, etc.), and other synchronizers.  However, there are
several points where it differs:

 * Unison runs on almost any system with an OCaml compiler. Moreover,
   Unison works across platforms, allowing you to synchronize a
   Windows laptop with a Unix server, for example.

 * Unlike simple mirroring or backup utilities, Unison can deal with
   updates to both replicas of a distributed directory
   structure. Updates that do not conflict are propagated
   automatically. Conflicting updates are detected and displayed.

 * Unlike many network filesystems, Unison copies data so that
   already-synchronized data can be read and written while offline.

 * Unlike most distributed filesystems, Unison is a user-level program
   that simply uses normal systems calls: there is no need to modify
   the kernel, to have superuser privileges on either host, or to have
   a FUSE implementation.

 * Unison works between any pair of machines connected to the
   internet, typically communicating over ssh, but also directly over
   TCP.  It is careful with network bandwidth, and runs well over slow
   links such as PPP connections. Transfers of small updates to large
   files are optimized using a compression protocol similar to rsync.

 * Unison is resilient to failure. It is careful to leave the replicas
   and its own private structures in a sensible state at all times,
   even in case of abnormal termination or communication failures.

 * Unison has a clear and precise specification.

 * Unison is Free; full source code is available under the GNU Public
   License, Version 3.

## Contributing

Note that only a very small number of people are actively working on
maintaining unison.  An estimate is 2.5 people and 0.1 Full-Time
Equivalents.  This has a substantial impact on the handling of bug
reports and enhancement reports.  Help in terms of high-quality bug
reports, fixes, and proposed changes is very welcome.  Help in
answering mailinglist questions is also welcome.  Please do not answer
questions asked in the bug tracker, which is contrary to bug tracker
usage guidance.

See `CONTRIBUTING.md` for a longer discussion.

## Community

Unison activity is now centered on the two [Unison
mailinglists](https://github.com/bcpierce00/unison/wiki/Mailing-Lists)
for discussion and [Unison's github
page](https://github.com/bcpierce00/unison/) for code, issues and a
wiki.

The `unison-users@` list is appropriate for asking for help.  The
`unison-hackers@` list is appropriate for discussions where
participants might be reading source code in order to inform the
discussion.

A no-longer-maintained FAQ can be found at: the [old UPenn
site](http://www.cis.upenn.edu/~bcpierce/unison).

## Getting Unison

The Unison project provides Unison as source code.  Many packaging
systems (including GNU/Linux distributions) provide binary packages of
Unison.  Results from Continuous Integration builds, while performed
for the purposes of testing, are available for use on a limited set of
platforms.

See the [building instructions](INSTALL.md), or read the CI
recipes.  (Currently, this is probably less well explained than it
should be.)

You may be able to find a pre-built binary for your operating system,
version, and CPU type.  For a list of sources, See
https://github.com/bcpierce00/unison/wiki/Downloading-Unison

You should use the most recent formal release, or a newer version from
git.  Earlier versions are no longer maintained, and bug reports are
not accepted about these versions.  This is true even though many
packaging systems (including GNU/Linux distributions) continue to have
2.51 or even 2.48.  The master branch in git historically has been
quite stable.

### Compatibility with old and unmaintained versions

For Unison versions 2.52 and newer, see
https://github.com/bcpierce00/unison/wiki/2.52-Migration-Guide

The information below is true for Unison versions older than 2.52.

Beware that Unison uses OCaml's built-in data marshalling, and that
this facility is unstable across versions of "ocaml" (the standard
implementation of the OCaml language).  Additionally, Unison has
incompatible changes across minor releases (e.g. 2.48 vs 2.51, but
2.51.2 and 2.51.3 are compatible).  Therefore, you must use the same
Unison minor version built with the same ocaml version on all systems.
