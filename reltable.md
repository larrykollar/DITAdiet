---
author: Larry Kollar
publisher: Oje Media
ID: reltables
---

# Relationship Tables

Practically speaking, relationship tables establish cross-links
between two or more topics.

At first, it seems more logical to insert links
into the topics themselves,
but topic reuse means that linked topics might not be included in every book.

For example, a user's guide includes a task that refers to a `setup` command.
That and other commands are fully documented in an appendix.
Later, a troubleshooting guide could reuse the command descriptions
but not include the task.
If the links are part of the topic files, this would result in broken links.

A relationship table (reltable) eliminates this problem
by specifying relationships specific to the book (or other topic collection).
You can either add the reltable to a map file after the topicrefs,
or link to a file containing the reltable.

Most online reltable examples use "concept/task/reference" column headings.
That can be misleading, making people think that is the only way to set up reltables.
Instead, eliminate the optional column headings and let your
reltables reflect the purpose of the book.
Use functional groups like:

* chapters
* audience (end-user, technician, field service)
* function (administration, installation, troubleshooting)
* product lifecycle phase (setup, using, upgrading, deleting)

Add columns for overview and reference information if needed.

A few other things to note:

* A reltable can have as many columns as needed.
  Too many columns may make the table hard to maintain, though.
* Topics inside the same cell do not refer to each other, unless grouped as a family.
  To do this, wrap the topicrefs in a `<topicgroup collection-type="family">` element.
  You can group some cell content and not others.
  For example, you might *not* group tasks that must always be performed in sequence,
  since your final step in one task would be to proceed to the next.
* Cells can be empty.
  That can either indicate a topic is unneeded in that column, or one needs to be written.
* When published, the DITA-OT automatically adds cross-references between topics in the same row.
  You can change this behavior on a case by case basis:
  * If you want to make a topic a destination-only link
    (that topic is pointed to, but does not point back),
    add the attribute `linking="targetonly"` to its topicref.
  * To do the opposite (the topic points to others but is not pointed to),
    add the attribute `linking="sourceonly"` to the topicref.
  * For more complex situations, where you want a topic to have links to topics not in one row,
    you can add the topic to another row.
* You can embed the reltable at the end of your bookmap,
  or place it in a separate map file and use the conref mechanism
  to include it (remember to assign the reltable an `id` attribute in this case).
  If you have multiple books sharing content,
  using the separate map file can help keep things consistent.
