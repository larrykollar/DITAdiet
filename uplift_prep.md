---
author: Larry Kollar
publisher: Oje Media
---

# Preparing a Book for Uplift {#upliftprep .task}

Converting an MDITA-based LwDITA project to full DITA
requires some preparation.
Much, but not all, of the preparation can be automated.
Be ready to override mistakes when necessary.

1.  Do a global search and replace in the bookmap:
    * Search: `format="mdita"`
    * Replace: `format="markdown"`

2.  Move the ID in MDITA files to the topic title.

    The *awk* script below is an example of how this can be done automatically.
    Wrap it in a shell script to loop over all the Markdown files in the book.

    ```awk
    NR == 1 && /^---/ { print; heading = 1; next; } # test for a heading

    /^ID:/ && heading {
      id = $2; next; # save the ID and eliminate it from the heading
    }

    /^---/ { heading = 0; print; next; } # in case a content line starts with "ID:"

    /^# / && id { # level 1 heading gets the ID, skip if no ID was found in metadata
      print $0, "{#" id "}"; next;
    }

    { print } # everything else gets passed through
    ```

3.  Categorize each topic as one of:
    * `concept` (information *about* an object or process)
    * `task` (*how to* do something)
    * `reference` (information *referred* to regularly)
    * `topic` (introductory content that doesn't fit in other categories)

    The primary difference between `concept` and `reference`
    is that you might only look at a concept once,
    but return often to reference topics.

    Categorizing topics can be at least partially automated.
    See [Tips for Automating Information Typing](uplift_infotype.md).

4.  Assign each topic a topic type on the topic title line:
    - `{.concept}`
    - `{.task}`
    - `{.reference}`

    The topic ID shares the brackets with the topic type,
    so your topic title might look like this:

    ```markdown
    # Doing the Thing {#dothing .task}
    ```

5.  Use the DITA-OT to convert the topics:

    ```sh
    dita --input=book.ditamap --output=out/dita --format=dita --args.rellinks=nofamily
    ```

    The converted files can be found in the subdirectory `out/dita`.
    Note that the converted topics still have an `.md` extension
    (more precisely, DITA-OT preserves the extension
    you used in the original files).

6.  Inspect the DITA files to make sure the conversion worked.
    If needed, rename extensions (and update references accordingly).
