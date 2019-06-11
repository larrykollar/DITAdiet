---
author: Larry Kollar
publisher: Oje Media
ID: usemdita
---

# Using MDITA Topics

MDITA files are Markdown, beginning with a metadata block.
MDITA can also use HDITA (HTML5) elements where raw Markdown
cannot provide the detail needed for a topic.

Use cases for MDITA include:

* Rapid composition is a primary concern.
* You receive contributed content in Markdown format.
* Writers sometimes need to work from mobile devices such as tablets
  (on which Markdown-aware editors are available, but HTML/XML editors are not).
* You want to enforce a minimalist style.
* You have to share topics with a Markdown-based publishing system
  like [Jekyll](http://jekyllrb.com/).

Reasons you may prefer another LwDITA format include:

* Your formatting requirements are more complex than MDITA can handle
  (for example, tables with block content).
* You need to share XML or HTML source files with outside entities.

You can draft topics in MDITA, then uplift them to HTML or full XML when needed.

## Example
In the following example:

* All metadata is at the top of the file,
  surrounded by lines containing three hyphens each.
  This is a YAML format block,
  making MDITA files useable in Jekyll without modification.
  MultiMarkdown supports this format as well.

* The metadata block is optional.
  Without it, LwDITA generates an ID from the topic title.

* The first paragraph becomes the `<shortdesc>` when converted to DITA.

```markdown
---
id: install-feechurr-client
source: 'http://dev.example.com/feechurr/installer/index.html'
author: Betty X. Empel
audience: enduser
---

# Installing the Feechurr Client
The Feechurr installer walks you through
the steps of installing the Feechurr client.

To install the client:

1. Double-click the Feechurr Installer package.
2. Follow the instructions on your screen.
```
