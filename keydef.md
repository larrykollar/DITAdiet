---
author: Larry Kollar
publisher: Oje Media
---

# Setting up Keydefs

Keydefs provide a way to insert and resolve variable data in topics.
This makes reusing topics easier, because you can easily change (for example)
a product name or model number without changing the topic.

You define keydefs (a/k/a *variables*) in the book map,
either directly or by creating a separate map file
and using the `<mapref>` element to refer to it.
Each method has certain advantages:

* If you have a set of related documents, create a separate map and reuse it.
* For variables unique to one document, add them to the book map.

Each `<keydef>` is a series of nested elements,
defining its name and value:

```xml
<keydef keys="prodname">
    <topicmeta>
        <keywords>
            <keyword>Feechurr</keyword>
        </keywords>
    </topicmeta>
</keydef>
```

In your XDITA topics, use the following element to insert the variable:

```xml
<ph keyref="prodname"/>
```

In HDITA and MDITA topics, use this element:

```xml
<span data-hd-keyref="prodname"/>
```
<p data-conref="0_reuse.md#reusesnips/htmlinmd"/>
