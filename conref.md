---
id: useconref
author: Larry Kollar
publisher: Oje Media
---

# Using Conrefs

Content references (conrefs) allow reusing block-level elements
such as paragraphs, list items, lists, or tables.

A content reference consists of two parts:

* A *target* block element with a unique ID.
* One or more *references*,
  a paragraph with a `conref` attribute pointing to the target ID.

In all topic types—XDITA, HDITA, and MDITA—tag a reusable block element with a unique ID.
For example:

    <p id="open-dialog">To open a file, select **File**&rarr;**Open**.</p>

Since list items and table cells in XDITA and HDITA must contain paragraphs,
this is the most flexible way to define a reusable block element.

To insert that reference into another file in XDITA, use an element like this:

    <p conref="filename.ext#fileid/open-dialog"/>

In HDITA and MDITA topics, use this format:

    <p data-conref="filename.ext#fileid/open-dialog"/>

<p data-conref="0_reuse.md#reusesnips/htmlinmd"/>

Note the reference structure—it requires the file name, the topic (top-level) ID,
and then the ID of the paragraph.<!-- why the eff they didn't use Xinclude for this... -->

**Tip**: You can place conref elements in a separate file,
and use `<topicref>` to include it without the content appearing out of place:

    <topicref href="snips.md" format="mdita" processing-role="resource-only"/>

The `@processing-role` attribute prevents the topic from being printed.
