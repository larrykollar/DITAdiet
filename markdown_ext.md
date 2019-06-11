---
author: Larry Kollar
publisher: Oje Media
source: https://github.com/jelovirt/org.lwdita/wiki/Syntax-reference
ID: markdown_ext
---

# Markdown Extensions

In the ditamap, if you specify `format="markdown"` instead of `format="mdita"`
in topicrefs, the LwDITA plugin enables several extensions.

The following sections list the most important extensions.
For a complete list, see the
[LwDITA Syntax Reference](https://github.com/jelovirt/org.lwdita/wiki/Syntax-reference).

## Specify Topic Types

When converting MDITA topics to DITA, the default action is to convert each topic
to the generic `topic` topic type.
You can specify topic types by including a special tag on the title line:

```markdown
# Installing the Feechurr Client {.task}

context...

1.  first step
2.  second step
```

If you are writing MDITA topics
with the intent to convert them to full DITA later,
this can be very useful.
The LwDITA plugin supports `concept`, `task`, and `reference` types.
With no tag, LwDITA creates a generic `topic`.

## ID specification

In `markdown` mode, LwDITA copies an `ID` tag in the header
into the DITA `prolog` block, and uses the title to generate an ID.
To specify an ID, include it on the title line:

```markdown
# Installing the Feechurr Server {#inst_svr .task}

context...

1.  first step

    step info

2.  next step
```

## Level 2 Heading Treatment

In both MDITA amd Markdown modes, level 2 headings begin a nested topic.
You can use a `{.section}` tag to specify `<section>`,
or `{.example}` for an `<example>`.
You can also use the pound sign (hashtag)
to specify an ID for the section or example, if you want:

```markdown
## Example {#some_example .example}
```

## Setting an `@outputclass`

If you prefer to set an `outputclass` on a topic,
instead of specifying a type, you can use the same tag construct
to specify an outputclass:

```markdown
# Topic Title {.specialclass}

etc...
```

A custom plugin can use this information to format the topic
or require specific elements.
