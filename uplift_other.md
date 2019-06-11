---
ID: upliftother
author: Larry Kollar
publisher: Oje Media
---

# Converting Other Documents to LwDITA

"Out with the old, in with the new"
would be an ideal way to approach a conversion.
In the real world, you have active projects
that need to be converted in minimal time
so you can keep working without missing a deadline.

How you should approach a conversion
depends heavily on your former document format:

* If you are already using HTML5 or Markdown as your primary file format,
  you can proceed with minimal changes.
  Markdown, for example, might require a YAML header for metadata.
* Word processor files, like Word or LibreOffice,
  can be converted to Markdown or HTML5 using [Pandoc](http://pandoc.org/).
  To convert to MDITA, output to `markdown` (Pandoc's Markdown),
  `markdown_mmd` (MultiMarkdown), or `gfm` (GitHub-Flavored Markdown),
  as they are nearly identical to MDITA.
  If one output does not work well, try another.

  **Note**: Always use the `--atx-headers` option to get the headers right.
  <!-- setext headers need to die in a fire -->
* Page layout systems can export articles to a word processor format,
  which can then be treated as a Word or LibreOffice document.
* Docbook can also be converted with Pandoc.
  Note that Pandoc recognizes only a subset of metadata found in the `<info>` block.
  If the results are not satisfactory, you may want to invest in an OxygenXML license
  and take advantage of its built-in Docbook to DITA conversion.
  If your Docbook HTML transform includes metadata,
  you may be able to repurpose the output as HDITA.
* XML-based content management systems, or those that export their own flavor of XML,
  are best converted using XSLT.

In extreme cases, a PDF may be the only thing available.
Unfortunately, that extreme case may not be rare.
Losing document source can happen for a number of reasons.
There are several ways to extract content from a PDF:

* If Acrobat Pro is not available to convert a PDF to Word
  or some other common format, Ghostscript's `ps2ascii` utility
  can at least extract the text from a PDF.
* Ghostscript has a driver that optionally outputs font changes, page breaks,
  and positioning information in XML format;
  that information may be useful for applying formatting.
* The open-source [mupdf](https://artifex.com/products-mupdf-overview/)
  utility can convert PDF files to HTML, text, XML, and a variety of other formats.
  The XML requires further processing to make it useful.
