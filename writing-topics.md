---
author: Larry Kollar
publisher: Oje Media
ID: writing_topics
---

# Writing Topics

The point of both DITA and LwDITA
is to work with documents as a collection of *topics*.

> A topic is a discrete piece of content that is about a specific subject,
has an identifiable purpose, and can stand alone
(does not need to be presented in context for the end-user to make sense of the content).  
> [[Topic-based authoring]]

One way to think of it:
instead of a novel, with a plotline and narrative,
you are writing a cookbook.
Each topic stands by itself,
referring to other topics as necessary.
For example, a pizza recipe refers to separate recipes
for the crust and sauce.
There may be several choices for both.

One advantage of splitting documentation into individual topics
is the potential for *reuse*.
Instead of copying/pasting the same information multiple times,
then trying to find all those instances later for an update,
you write once and refer to that one instance as necessary.
In the cookbook example,
recipes for garlic breadsticks or focaccia could reuse the crust recipe.
Likewise, one or more pasta dishes reuse the sauce recipe.
<!-- are we hungry yet? -->

Reuse in LwDITA is not limited to topics, though.
More on that shortly.

In full DITA, you would then engage in [information typing]—categorizing topics into task, concept, reference, or troubleshooting types.
In LwDITA, there is only the generic topic.

[Topic-based authoring]: https://en.wikipedia.org/wiki/Topic-based_authoring

[information typing]: https://docs.oasis-open.org/dita/v1.0/archspec/infotypes.html
