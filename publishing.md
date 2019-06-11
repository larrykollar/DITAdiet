---
id: publishing
author: Larry Kollar
publisher: Oje Media
---

# Publishing LwDITA Documents

One of the strengths of DITA, and LwDITA by extension,
is the ability to publish your books to a number of different formats.

To publish your book from the command line, use:

    dita --input=mapfile.map --format=[name]

Replace `mapfile.map` with the name of your bookmap or ditamap,
and `[name]` with one of the following output formats:

* pdf2
* html5
* xhtml
* dita
* markdown

This is not an exhaustive list.
The [DITA-OT website](http://www.dita-ot.org/3.3/topics/output-formats.html)
provides a complete list of formats,
and [plugins are available for other formats](https://github.com/dita-community/dita-community-ot-plugins).
To see the output formats installed on your system,
use a nonsense format string like `xyz`.

**Tip**: In DITA-OT 3.2 and newer, you can use the `--transtypes` option
to display the available output formats.

During the publishing process, the DITA-OT converts all LwDITA files
to DITA topics, then processes them as normal DITA files.

**Tip**: In Oxygen, you can publish from the editor (bypassing the command line)
by using one of the included transformation scenarios.
You can modify existing scenarios, or create new ones, if needed.
