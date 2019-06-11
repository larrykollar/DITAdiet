---
id: mdita_extend
author: Larry Kollar
publisher: Oje Media
---

# MDITA Extensions and Constraints
The LwDITA plugin supports several extensions for MDITA topics,
not found in the proposed LwDITA specification.
Depending on the version of the LwDITA plugin you are using,
there may be a few issues to work around.

## Standard Markdown Syntax Support

Text surrounded by backticks
is standard Markdown syntax for a code phrase.
The LwDITA extension recognizes it, treating it as a DITA `<codeph>` element.

Example:

    Type `feechurr` at the command line to run Feechurr.

## Free-floating URLs

In versions 2.0.2 and earlier of the LwDITA plugin,
free-floating URLs (that is, those outside links or code blocks)
cause fatal errors when publishing.

```
Go to <http://dita-ot.org/> <!-- this doesn't work -->
Go to http://dita-ot.org/ <!-- neither does this -->
Go to the [DITA-OT website](http://dita-ot.org/). <!-- OK -->
```

**Note**: DITA-OT 3.1 includes version 2.0.5 of the LwDITA plugin,
which fixes this issue.

## Code Block Constraints and Extensions

In versions 2.0.8 and earlier of the LwDITA plugin,
indenting code blocks causes the first line in the block to appear flush-left,
and the others indented.
This is not a problem for one-line blocks,
but you should use the three backticks construct (```)
for multi-line code blocks.
Version 2.2 of the LwDITA plugin fixes this issue.

If you add a text string after the backticks (for example, ```markdown)
the string becomes part of the `outputclass` attribute for the code block.
Some Markdown processors use this construct for syntax highlighting.
Custom plugins could use it as well.
