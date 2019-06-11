---
author: Larry Kollar
publisher: Oje Media
---

# Getting Started

There are three primary software components you need to start using LwDITA.

## DITA Open Toolkit (DITA-OT)

Version 3.0 of the DITA Open Toolkit was the first version
to provide built-in support for LwDITA.
Version 3.1 fixes some critical issues and further refines LwDITA support.
Version 3.2 adds support for XDITA, the simplified XML topic type.
As LwDITA is still under development, it's billed as "preview support."
There may be some minor changes in future releases.
Later editions of this book will attempt to track future changes as they happen.

But enough of that.
Download the latest version of DITA-OT from [the DITA-OT site](http://dita-ot.org/).
You need a fairly recent version of Java on your computer to run it.

<!-- xxx something here about oxygen pdf chemistry? -->

If, for whatever reason, you cannot use the latest DITA-OT,
older versions work with some limitations.
You need to install the plug-in separately, though.
Download these components:

* DITA-OT 2.2 or newer, from the [DITA-OT downloads page](http://www.dita-ot.org/download)
  (versions 2.5.4, or 3.1 and newer, are recommended)
* The newest `org.lwdita` plugin from the [LwDITA Github page](https://github.com/jelovirt/org.lwdita);
  scroll down to find installation instructions.

There is also a `dita-ot-markdown` plugin; it predates `org.lwdita` and supports only Markdown.
It has been deprecated in favor of the `org.lwdita` plugin.

## Editor

You need a text editor that understands the LwDITA formats you plan to use.
The editors suggested below work with all currently supported formats,
and are cross-platform.

* [OxygenXML Editor](http://oxygenxml.com/) (expensive, but very good, with excellent support)
  * Versions 19.0 (at least) and newer bundle DITA-OT 2.5.4
    (with the `dita-ot-markdown` plugin pre-installed).
    Changing that to DITA-OT 3.1 or newer can be done in the application preferences.
  * Install the [Oxygen Git Plugin](https://github.com/oxygenxml/oxygen-git-plugin)
    if you plan to work with Github or a Git repository.

* [Atom](http://atom.io/) (Free, works well, Git integration built in). Add these plugins:
  * Trailing Spaces
  * Linter-xmllint

* [Brackets](http://brackets.io/) (Free, works well, supports 32-bit systems).
  Add these plugins:
  * Markdown Preview
  * Brackets Git
  * HTML Format
  * Trailing Spaces

This book uses Atom in examples.

## Source Repository

A repository, also called a *version control system*,
allows multiple writers to edit topics without fear that another writer
might overwrite it.
If Phoebe and Ben both check out `intro.dita`, and make changes,
the system attempts to merge them together and flags any conflicts.

Just as important, a repository tracks change history and allows *rollback*
if a change later needs to be reverted.

The corporate IT department should be able to set up a repository for the writers.
If that is not feasible, or a small number of writers want to try a pilot project,
[Github](http://github.io/) offers free public hosting and low-cost private hosting.
