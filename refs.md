---
author: Larry Kollar
publisher: Oje Media
ID: reuse
---

# Reuse and References

One of DITA's strengths is *reuse*,
the ability to pull a topic, block (lists, paragraphs, and tables),
or phrase into different parts of your document as needed,
or into different documents.
LwDITA supports reuse as well.

Examples of candidates for reuse include:

* Boilerplate information, such as copyright or trademark information,
  that must be consistent across documents
* Cautions or warnings that appear frequently in instructions
* Product names or model numbers,
  especially in topics used in multiple documents (document variables)
* Steps, duplicated across multiple tasks.

LwDITA adopts two DITA mechanisms for reuse:

* Content references (conref)—reuses block content.
  The block to be reused must have a unique `id` attribute.
* Key references (keyref)—equivalent to document variables.

Later chapters, documenting each supported format,
provide details about using references.

**Tip**: You can collect reusable paragraphs into a separate file,
making them available to related documents.
You must define key references in the bookmap.
