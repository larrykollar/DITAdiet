---
author: Larry Kollar
publisher: Oje Media
ID: workmaps
---

# Working with Maps

In DITA-speak, a *map* is a collection of topics (and other maps).
Maps can be used as “book” files, or to group topics related to a single chapter or feature.

While LwDITA specifies several ways to collect topics,
DITA maps are flexible and simple enough for general use.
They provide the added advantage of being able to mix
full-weight DITA topics and LwDITA topics.

DITA maps are XML files, usually with a `.map` or `.ditamap` extension.

## Map Contents

A map begins with a `<title>` element that becomes a book or chapter/section title,
depending on its position.
Following the title is one or more `<topicref>` or `<mapref>` elements,
each representing a topic or map to include.
Note that topicrefs can contain other topicrefs and maprefs.

A map can also contain a relationship table (reltable),
which specifies which topics are related.
See [Relationship Tables](reltable.md) for details.

Bookmaps are more elaborate, supporting metadata, front (and back) matter,
and a way to differentiate chapters and appendices.
LwDITA currently works with both maps and bookmaps.

## Example Map
The following is an example of a DITA map.

```xml
<?xml version="1.0" ?>
<map>
    <title>DITA on a Diet: Using Lightweight DITA</title>

    <topicref href="intro.md" format="mdita">
        <topicref href="solution-lwdita.md" format="mdita"/>
        <topicref href="why-adopt.md" format="mdita"/>
    </topicref>

    <topicref href="getstart.md" format="mdita">
        <topicref href="writing-topics.md" format="mdita"/>
        <topicref href="refs.md" format="mdita"/>
    </topicref>
</map>
```

Note the `format` attribute on each `topicref`.
LwDITA extends the allowed values for `format`,
specifying the format of the file.
This is required for LwDITA to process the topics.
Supported LwDITA formats are:

| Name | Format |
| ---- | ------ |
| `mdita` | Markdown (strict LwDITA parsing) |
| `markdown` | Markdown (lenient parsing, see [Markdown Extensions](markdown_ext.md)) |
| `hdita` | HTML5 |
| `xdita` | XDITA (DITA topic) |
