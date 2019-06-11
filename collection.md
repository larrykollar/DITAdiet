---
id: collection
author: Larry Kollar
publisher: Oje Media
---

# Using Collections

If you are using DITA maps to structure your book,
collections are easier than reltables for specifying relationships.
On the other hand, collections are effective only between parent and child topics.

To set up a collection, add the `collection-type` attribute
to a `topicref `item in your bookmap.
The attribute can have one of the following values:

* `unordered`—Links between a topic and its children, not between children.
* `family`—Links between all child topics in the collection.
* `sequence`—Links between a topic and its children, and between adjacent children.
* `choice`—Used when a reader needs only one of a set of child topics
  (for example, replacing a battery in one of a group of products).
  DITA-OT renders links for `choice` in the same manner as for `unordered`.

If you only want, for example, links from the parent to child topics
in unordered or family collections
(but not vice versa), add the attribute `linking="sourceonly"` to the `topicref`.
