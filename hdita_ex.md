---
author: Larry Kollar
publisher: Oje Media
ID: usehdita
---

# Using HDITA Topics

HDITA files are HTML5, with a few constraints.
HDITA is otherwise completely interchangeable with HTML5.

Use cases for HDITA include:

* You are adapting a large body of HTML5-based documentation
  (which you may have to rewrite as topics).
* Your writers are already familiar with HTML.
* HTML (or webhelp) is your primary deliverable.
* You need complex tables
  (of the currently supported formats,
  only HDITA supports spanning rows).
* Your deliverables include rich media, such as video or audio.
* You need to interchange topics with other groups using HTML or HDITA.

Reasons you may prefer another LwDITA format include:

* You plan to move to full DITA over time.
* Any HTML you inherit or receive from other sources requires extensive rewrites,
  so there is no advantage to keeping it in that format.

You can convert HDITA topics to full XML when needed.

## Example

In the example HDITA topic below:

* HDITA topics use the `<article>` element as a container for the content and the ID.
  Other metadata appears in `<meta>` elements in the HTML head.

* The first paragraph is the short description.

* All text inside the `<body>`, except for the heading, is wrapped in paragraph elements.

```html
<html>
  <head>
    <title>Installing the Feechurr Client</title>
    <meta name="author" content="Betty X. Empel"/>
    <meta name="source"
      content="http://dev.example.com/feechurr/installer/index.html"/>
    <meta name="audience" content="enduser"/>
  </head>
  <body>
    <article id="install-feechurr-client">
      <h1>Installing the Feechurr Client</h1>
      <p>The Feechurr installer walks you through the
          steps of installing the Feechurr client.</p>

      <p>To install the client:</p>
      <ol>
        <li><p>Double-click the Feechurr Installer package.</p></li>
        <li><p>Follow the instructions on your screen.</p></li>
      </ol>
    </article>
  </body>
</html>
```
