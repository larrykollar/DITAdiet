---
id: topic_metadata
author: Larry Kollar
publisher: Oje Media
---

# Topic Metadata

Metadata can be thought of as a second document,
embedded in the topic or bookmap.
Its target audience is computers—search engines,
publishing processors, and other software that helps computers
serve the human audience.
Common metadata components include:

* `ID`—a string that uniquely identifies the topic.
  Some publishing systems generate IDs for you;
  others expect you to keep them straight.
  If a topic has no ID, DITA-OT generates an ID using the title content
  (another good reason to make titles unique).

* `shortdesc`—a short description of the topic.
  Search engines often display this text
  to help readers determine whether the topic is relevant.
  Links set up by collections and relationship tables
  include the short description, if one exists.
  LwDITA uses the first paragraph of an MDITA or HDITA topic
  as the shortdesc.

* `prolog`—a collection of miscellaneous data.
  Common prolog metadata includes:
  * author (author name)
  * publisher (publisher name)
  * source (reference to source material)
  * permissions (who is allowed to view or modify the document)
  * audience (the target audience of the topic)
  * category (one or more categories, used to group topics for navigation or search)
  * keyword (helps search engines narrow down relevant topics)
  * resourceid (used to integrate documentation with a software product)

  HDITA topics can use the `<meta>` element to define these and other metadata.
  MDITA and Markdown topics support them in the metadata block at the top of the topic.

* `outputclass`—information passed to the publishing system
  that explains how to treat a topic (or elements with an `outputclass` attribute).
