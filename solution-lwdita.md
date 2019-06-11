---
author: Larry Kollar
publisher: Oje Media
ID: solution
---

# One solution: LwDITA

Lightweight DITA (LwDITA) is one way to gain many of the benefits of structured authoring,
while continuing to use familiar file formats and avoiding much of the complexity
of a full-weight DITA solution.

LwDITA is a:

> … simplified version of (DITA). …
> LwDITA has a smaller element type and attribute set, stricter content models,
> and a reduced feature set. LwDITA also defines mappings between XML, HTML5,
> and Markdown, enabling authoring, collaboration, and publishing
> across different markup languages.  
> [*Lightweight DITA: An Introduction* Version 1.0. Edited by Carlos Evia, Kristen James Eberlein, and Alan Houser. 10 April 2018. OASIS Committee Note 01.](http://docs.oasis-open.org/dita/LwDITA/v1.0/LwDITA-v1.0.pdf)

LwDITA addresses the needs of documentation groups who want
the benefits of topic-based authoring, without a lengthy conversion and training process.

One of the visionary aspects of LwDITA is its embrace of non-XML formats,
allowing immediate adoption.
Currently, LwDITA supports:

* XDITA (XML format, a "lite" version of DITA's generic topic)
* HDITA (HTML5 format, supports media objects)
* MDITA (Markdown, can use HDITA elements as fallback)

In addition, LwDITA can use DITA `<map>` and `<bookmap>` doctypes to create books
and collections of related topics.
Mixing LwDITA and full-weight DITA topics in the same map is supported.
Future LwDITA specifications may introduce new formats,
expanding its reach even further.
