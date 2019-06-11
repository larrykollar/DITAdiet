---
ID: custom_html
author: Larry Kollar
publisher: Oje Media
---

# Customizing HTML Output

Creating a custom XHTML plugin is far easier than PDF,
usually requiring only a few boilerplate control files
and a CSS file.

The instructions here borrow from the
[Bundling CSS in a custom HTML plug-in](http://www.dita-ot.org/3.3/topics/html-customization-plugins.html)
instructions at the DITA-OT website,
but provide a more complete example.
In this example, we:

* create a plugin called `com.example.html` that is invoked using `--format=ex-html`
* build some custom styles
* set up control files as necessary to invoke the custom CSS
* set up a TOC column, a content column, and a banner (header)

1.  Set up your plugin hierarchy, using blank files. It should look like this:
    ```
    com.example.html/
      css/
        ex-styles.css
      build.xml
      plugin.xml
    ```
2.  Add styles to the `css/ex-styles.css` file as desired. The following is an example.
    ```css
    /* optimized for DITA-OT HTML5 output */

    .pre, pre.screen {
      padding: 0.4em;
      background-color: #efefef;
      font-family: monospace;
      overflow: scroll;
    }

    .body {
      font-family: Bookman, serif;
      font-size: 11pt;
      padding: 2%;
    }

    .p {
      margin-top: 0.6em;
    }


    /* put nav TOC on the left */
    nav {
      font-family: sans-serif;
      display: block;
      float: left;
      width: 32%;
      background-color: #ddddf1;
      padding: 1%;
    }

    /* related links navs use the whole 2nd column */
    nav.related-links {
      width: 100%;
      float: none;
    }

    main {
      float: left;
      width: 65%;
    }

    article {
      margin-left: 0.8em;
    }

    /* header/footer */
    div.header {
      background-color: #eeeeee; /* to show its extent */
      padding: 12px;
      border-bottom: solid black 1px;
    }

    div.footer {
      clear: both; /* get past the floats */
      font-size: 11pt;
      padding: 12px;
      border-bottom: solid black 1px;
    }
    ```

    The XHTML plugin uses elements for major blocks, and classes to format output.
    Look at the file `org.dita.xhtml/resource/commonltr.css` (or `commonrtl.css` if needed)
    to see how common DITA elements are formatted.
    You can also make broader changes by element type.
3.  Edit the file `plugin.xml` and set it up as follows.
    This file is the master file of your plugin, setting up the other files as needed.
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <plugin id="com.example.html">
      <require plugin="org.dita.html5"/>
      <feature extension="dita.conductor.transtype.check" value="ex-html"/>
      <feature extension="dita.conductor.target.relative" file="build.xml"/>
    </plugin>
    ```
4.  Edit the file `build.xml` and set it up as follows.
    This file sets properties, including the name of your custom CSS file.
    ```xml
    <?xml version='1.0' encoding='UTF-8'?>
    <project name="com.example.html">
      <target name="dita2xhtml-ex">
        <antcall target="dita2xhtml">
          <!-- Custom .css file used to style output -->
          <param name="args.css"
            value="${dita.plugin.com.example.html.custom.css.dir}/css/ex-styles.css"/>
          <!-- Copy the custom .css file to the output directory -->
          <param name="args.copycss" value="yes"/>
          <!-- Location of the copied .css file relative to the output -->
          <param name="args.csspath" value="css"/>
        </antcall>
      </target>
    </project>
    ```
    The following names must match:
    *  the plugin ID in `plugin.xml` and the project name in `build.xml`
    *  the plugin directory name and the middle part of the `args.css` value in `build.xml`
    *  the CSS file name specified in `build.xml` matches your CSS file

5.  Copy the plugin directory to `plugins` in your DITA-OT directory,
    then run `dita --install` to set it up.

    If you change the XML files at the top level, you should run `dita --install` again
    to make sure the changes get picked up.

6.  The plugin's CSS is designed to put a navigation TOC in the left column.
    To include a TOC, set up your command line like this:
    ```sh
    dita --output=ex-html --input=my.bookmap -D nav.toc=partial
    ```
7.  To add a banner across the top of the page, create the file `hdr.xml`
    and set it up:
    ```xml
    <div class="header">
      <h1>Document title</h1>
      <p>Author, description, etc.</p>
    </div>
    ```
8.  Now format again, using the following command line:
    ```sh
    dita --output=ex-html --input=my.bookmap -D nav.toc=partial -D args.hdr=/path/to/hdr.xml
    ```

    Note that `args.hdr`, `args.ftr`, and `args.css` must be full paths.
    Specify them in a .properties file to avoid typing errors.
