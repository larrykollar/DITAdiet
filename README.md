# DITA on a Diet: Setting Up and Using Lightweight DITA (LwDITA)

Topic-based, structured authoring has well-known benefits,
but traditionally require high-end XML-based publishing systems.
The costs to acquire and support those systems
place them out of reach for many documentation departments.

Lightweight DITA (LwDITA) is changing that.
Write your topics in HTML5 or Markdown,
and use the standard [DITA Open Toolkit](http://dita-ot.org/)
to publish.
Markdown and HTML5 topics are co-equal with full-weight DITA topics,
allowing SMEs to contribute content in familiar formats
for departments with a DITA-based publishing system.

In this small 68-page (PDF) book,
Larry Kollar shows you how to set up and deploy
an LwDITA publishing system using open-source tools.

The PDF is available in the Release section, or
[download it](https://github.com/larrykollar/DITAdiet/releases/download/v1.0/lwdita.pdf)
directly.

## Building the book

To build the book from source, you need:

*  [DITA Open Toolkit](http://dita-ot.org/), v3.0 or newer.
   [Install](https://www.dita-ot.org/dev/topics/installing-client.html) the latest version if possible.
*  For PDF, use the [com.ojemedia.pdf69 plugin](https://github.com/larrykollar/com.ojemedia.pdf69).
   This is optional, but recommended.
   Copy the `com.ojemedia.pdf69` directory into `plugins` in the DITA-OT directory,
   then use the command `dita --install` to integrate it.
*  Edit the `lwd.properties` file in this directory, replacing the absolute path names
   with your own directory path.

### Build a PDF

    dita --input=lwdita.ditamap --propertyfile=lwd.properties --format=pdf69

If you are not using the `pdf69` plugin,
replace that with the proper format name for your PDF plugin.

### Build a set of static HTML pages

    dita --input=lwdita.ditamap --propertyfile=lwd.properties --format=html5 \
        --output=out/html

Open the HTML starting with `intro.html`.

**Note**: I ran into errors using DITA-OT 3.2.1. Versions 3.1 and 3.3.2 work, though.
