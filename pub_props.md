---
id: pub_props
author: Larry Kollar
publisher: Oje Media
---

# Setting Publishing Properties

You can make changes to various DITA-OT configuration properties
to override various defaults.
For example, if you prefer to omit the chapter TOC in PDF output,
set the property `args.chapter.layout` to **BASIC**.

The DITA-OT [Configuration properties](http://www.dita-ot.org/3.3/parameters/configuration-properties.html)
page provides five ways of setting properties.
In this book, we will focus on the simplest three ways.

See [DITA-OT parameters](http://www.dita-ot.org/3.3/parameters/parameters_intro.html)
for a list of all configurable properties by family.
For example, some properties apply to PDF and not XHTML, and vice versa.

Properties files have the following format:

```
# this is a comment
arg.name = value
```

## local.properties

If you have a set of properties you always want set,
for any documents you publish,
add them to a file called `local.properties`
in the root of the DITA-OT directory.
The next two methods can override these settings,
if you have special cases.

## Project Properties File

If you need a specific set of properties for one project,
create a properties file in the project directory.
You can all it anything you want, but the convention is to give it
a `.properties` extension.

So if you have a file called `mybook.properties`, you can call it
on the command line using the following option:

    --propertyfile=mybook.properties

If you have the same settings in this file and `local.properties`,
the settings in this file take precedence.

Your project properties file can specify properties
for both PDF and HTML.
The DITA-OT ignores property settings for all but the current output format.

## Command Line Property Settings

If you need to set a property once,
whether for testing or a special case,
there are two ways to specify it on the command line:

```
-D arg.name=value
--arg.name=value
```

The second form may not work for all properties.
Specifying a property on the command line overrides
any settings in both `local.properties` and a project-level properties file.
