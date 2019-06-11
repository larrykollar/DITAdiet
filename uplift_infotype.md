---
author: Larry Kollar
publisher: Oje Media
ID: infotype
---

# Tips for Automating Information Typing

Information typing—the process of identifying a topic's type—can be
at least partially automated.

The following examples may be helpful when writing scripts
to automate information typing.
You will likely have to change and add to the list for your documentation.
Always be ready to override the script, when you know better.

* Skip Markdown files that already have a topic type tag (like `{.task}`).
* Numbered lists usually indicate tasks.
* If the first word in the title ends with *ing*, the topic is often a task.
* Tables and definition lists often indicate a reference topic.
* The word *Commands* in the topic title suggests a reference.
* Sections tagged `{.example}` suggest a reference.
* Bulleted lists, and topic titles beginning with *About*, suggest concepts.
* If nothing else matches, use a generic topic (or a concept).
* Flag non-reference topics with more than one subsection;
  they may need to be broken up into individual topics.

Order can be significant—for example, if a topic contains a numbered list
and a table, the topic is probably a task (especially if the table is indented
under a step).
If time permits, examine the topics and override assigned types if needed.
