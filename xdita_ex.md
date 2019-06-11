---
id: usexdita
author: Larry Kollar
publisher: Oje Media
---

# Using XDITA Topics

XDITA is a simplified version of DITA's `topic` topic type.
DITA-OT 3.2 and newer versions provide native support for XDITA,
through the included `org.oasis-open.xdita` plugin.

Use cases for XDITA include:

* Authoring in an XML format, but with a limited set of elements and attributes
  that are easy to remember.
* Writing original content in a mixed environment,
  anticipating a future shift to full DITA.
* The need to exchange topics with other departments or partners using DITA.
* Working with complex topics that cannot be written comfortably in HDITA or MDITA.

Reasons you may prefer another LwDITA format include:

* Your writers (or their tools) are not equipped to work with XML formats.
* You need tables with `@rowspan` or `@colspan` attributes,
  which are not supported by the XDITA `<simpletable>`.
* You exchange source files with groups that do not use XML.

XDITA is, as one would guess, the closest of the three formats to full-weight DITA.

## Example

In the following example:

* The `DOCTYPE` declaration differentiates XDITA topics
  from full-weight DITA topic types.

* The `<prolog>` element contains metadata, except for the ID,
  which is an attribute of the `<topic>` element.

* Note that in the `<body>`, most text must be wrapped in `<p>` elements.
  This is true for paragraphs, list items, and table cells in LwDITA,
  but not in full DITA.
  However, the `<title>` and `<shortdesc>` elements do not require paragraphs.

```xml
<?xml version="1.0" ?>
<!DOCTYPE topic PUBLIC "-//OASIS//DTD LIGHTWEIGHT DITA Topic//EN" "lw-topic.dtd">
<topic id="install_feechurr_client">
    <title>Installing the Feechurr Client</title>
    <shortdesc>The Feechurr installer walks you through
      the steps of installing the Feechurr client.</shortdesc>
    <prolog>
        <data name="author" value="Betty X. Empel"/>
        <data name="source"
          value="http://dev.example.com/feechurr/installer/index.html"/>
        <data name="audience" value="enduser"/>
    </prolog>
    <body>
        <p>To install the client:</p>
        <ol>
            <li><p>Double-click the Feechurr Installer package.</p></li>
            <li><p>Follow the instructions on your screen.</p></li>
        </ol>
    </body>
</topic>
```

Other DITA constructs are supported, as follows.

Unordered lists:

```xml
<ul>
    <li><p>List item text</p></li>
    <li><p>Another list item</p></li>
    ...
</ul>
```

Definition lists:

```xml
<dl>
    <dlentry>
        <dt><p>Term</p></dt>
        <dd><p>Definition</p></dd>
    </dlentry>
    ...
</dl>
```

Sections:

```xml
<section>
    <title>Optional Title</title>
    <p>Some more information that goes in this section.</p>
    <p>Includes paragraphs, lists, and tables (but not other sections).</p>
</section>
```

Tables (simpletable):

```xml
<simpletable>
    <sthead>
        <stentry><p>Option</p></stentry>
        <stentry><p>Description</p></stentry>
    </sthead>
    <strow>
        <stentry><p>-c</p></stentry>
        <stentry><p>Cobbles the output files together in random order.</p></stentry>
    </strow>
    ...
</simpletable>
```

Images (block):

```xml
<fig>
  <title>Optional image title</title>
  <image href="../images/foo.jpg"><alt>Accessibility text</alt></image>
</fig>
```

Images (inline):

```xml
<image href="../icons/dwim.png"/>
```

Linked video (not terribly useful for PDF):

```xml
<video>
  <desc>Description</desc>
  <media-source value="https://www.youtube.com/embed/G0bB13dY-600K"/>
</video>
```

Cross-references use the `<xref>` element.

```xml
<xref href="some_topic.md#topicID"/>
<xref href="some_topic.md#topicID">link text</xref>
<xref href="http://example.com/feechurr/index.html" scope="external">An
  external reference</xref>
```

Notes and related admonitions (caution, warning, tip) use the `<note>` element.

```xml
<note>You need to do something here.</note>
<note type="caution">You probably shouldn't do this, though.</note>
<note type="tip">Use the format="markdown" attribute for a topicref
   to include a Markdown topic in your book map.</note>
```

Footnotes:

```xml
<p>The best way to do this<fn>This has not been tested.</fn> is to
pull the pin and see what happens.</p>
```

Inline text highlighting in XDITA is restricted to `<b>`, `<i>`, `<u>`,
and superscripts and subscripts (`<sup>` and `<sub>`).
The functionality is mostly equivalent to Markdown,
except that XDITA does not have `<codeph>`,
the equivalent to the backtick construct in Markdown.
If you need more structural markup, say for code snippets or citations,
use a `<ph>` element and set the `@outputclass` attribute.
Your transform can use this information to provide further highlighting.
