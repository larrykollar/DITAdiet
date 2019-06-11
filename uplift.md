---
ID: uplift
author: Larry Kollar
publisher: Oje Media
---

# Converting MDITA, HDITA, and XDITA Topics

LwDITA supports three different file formats,
and makes it easy to convert topics to any of the supported formats.

You can convert individual topics, or an entire book,
by specifying the topic or book file in the `--input` argument.
The `--format` argument can be any of:

* `dita`
* `xhtml`
* `markdown` (MDITA Markdown)
* `markdown_github` (GitHub Flavored Markdown)
* `markdown_gitbook` (GitHub Flavored Markdown with a SUMMARY.md file for GitBook)

One of the advantages of this feature is the ability to compose topics
in Markdown, then *uplift* them to HDITA or XDITA as needed.
Conversely, you can export XDITA topics to Markdown or XHTML to accommodate Jekyll
and other static site generators (although you may need to edit the result
before deploying).

**Note**: If you do not want topics to contain hard-coded relative links,
use the parameter `--args.rellinks=nofamily` when converting.

After converting a topic, look for the following:

* Links, keyrefs, and conrefs become hard-coded.
  This may be useful, if the converted topics must stand alone.
* Topics use the original extension.
  You may want to rename them, fixing any cross-references or topic references.
* Some topics may need cleanup
  (for example, complex formatting converted to Markdown).
* MDITA and HDITA natively support line breaks.
  For XML, LwDITA converts them to a `<?linebreak?>` processing instruction
  for both publishing and conversion.
  If necessary, modify your plugin to recognize it.
