---
id: pub_trouble
author: Larry Kollar
publisher: Oje Media
---

# Trouble?

The DITA-OT is robust,
and the simplicity of LwDITA files makes it even more so.
Often, publishing errors happen when
a map, or an XDITA or HDITA file,
is not [well-formed](https://en.wikipedia.org/wiki/Well-formed_element).
Errors in MDITA files tend to be self-limiting,
recovering at the next paragraph or block element.

Most publishing errors fall into one of two categories:

* complete failure, with an informative error message if you're lucky
* you get output, but not what you expected

When publishing from the command line,
the DITA-OT provides some information about what it's doing.
Add the `-v` (verbose) option to get detailed information.
If you enable this option, you should send the log messages to a file
so you can examine it in an editor.
So your command would look like this:

    dita --input=mapfile.map --format=pdf2 -v -l log.log

Doing this can help with both types of problems.

## Complete Failure

The most likely errors that cause a complete failure are:

* a missing or bad DOCTYPE in the map (or XDITA topic) file
* autocorrect turning three hyphens (`---`) into an emdash (—)
  in the metadata block of an MDITA file
* map, HDITA, or XDITA files not well-formed
* problems in a custom plugin
* PDF open in Acrobat Reader while trying to republish
  (Apple's Preview app does not have this problem)

**Note**: Certain versions of the LwDITA plugin do not support common
MDITA link shortcuts, quitting with a fatal error.
See [MDITA Extensions and Constraints](mdita_extension.md) for details.

One of the advantages of verbose logging is DITA-OT
tells you the page or topic where the error happened,
or if the error occurred before reaching the output phase.
Thus, if you don't know exactly what triggered the error,
you at least know where to start looking.

## Fontbox Error

If you are using a pre-3.0 DITA-OT,
most OpenType typefaces require a JAR named "Fontbox"
that is not included in DITA-OT's version of FOP.
Copying the JAR file into the toolkit is not sufficient
to correct the error.

You can either update your DITA-OT or specify non-OpenType typefaces.
If you are using the Oxygen editor, Fontbox has been installed
and you should not see this error.

## MDITA and HDITA Topics Missing

If none of the topics print, only the title page,
the `org.lwdita` plugin may not be installed.

If one or more topics are missing:

* verify the file name and path are correct.
* make sure the LwDITA format is included for each topic in the map file:
  `format="mdita"` (or `markdown`) for MDITA, and
  `format="hdita"` for HDITA.
* if you are using a map or bookmap,
  make sure any `<chapter>`, `<notices>`, `<appendix>`, and `<preface>`
  elements specify a valid file (using the `@href` attribute).

## Message "tools.jar not found"

This message can be safely ignored.
If it annoys you, replace your Java Runtime Environment (JRE)
with the Java Development Kit (JDK).

**Note**: DITA-OT 3.1 eliminates most of the chatter on the command line,
including this message,
so you should see only fatal errors and certain warnings.

<!-- ## Other Unexpected Output

Unexpected output can be both easier and trickier to figure out.
Some problems, like a text span not being closed properly, are obvious. -->
