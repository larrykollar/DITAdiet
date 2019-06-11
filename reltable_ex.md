---
id: reltable_ex
author: Larry Kollar
publisher: Oje Media
---

# Example Relationship Tables

You can use relationship tables in many different ways.
The DITA specification allows multiple reltables in a bookmap,
so you can keep separate tables to do different things.

A typical reltable looks like the following.
It sets up links to all the other topics in the same row.

```xml
<!-- this starts after the last topic in the map -->
<reltable>
    <!-- columns:
        overview
        setup
        usage
        reference -->

    <relrow>
        <relcell>
          <topicref href="about_feechurr.dita"/>
        </relcell>
        <relcell>
          <topicref href="feechurr_setup.dita"/>
        </relcell>
        <relcell>
          <topicref href="feechurr_using.dita"/>
        </relcell>
        <relcell>
          <topicref href="feechurr_settings.dita"/>
        </relcell>
    </relrow>

    <!-- more rows ... -->
</reltable>
```

By using the `linking="sourceonly"` attribute,
you can use reltables to set up an "In this chapter" list.
Such a table can be automatically built
by using an XSLT script to walk through the bookmap.

```xml
<!-- example "in this chapter" list -->
<reltable>
  <!-- columns:
      chapter
      top-level topics -->
  <relrow>
    <relcell>
      <topicref href="Installation.md" linking="sourceonly"/>
    </relcell>
    <relcell>
      <topicref href="required_tools.md"/>
      <topicref href="unpacking.md"/>
      <topicref href="assembly.md"/>
      <topicref href="testing.md"/>
      <topicref href="troubleshooting.md"/>
    </relcell>
  </relrow>

  <!-- more rows, one per chapter... -->
</reltable>
```

Topics describing tasks might refer to certain commands
used in the task, as well as related topics.
By using `linking="targetonly"`, the command topics
are not cluttered with links to irrelevant topics.

```xml
<!-- Feechurr links -->
<reltable>
  <!-- columns:
        concept
        tasks
        references -->
  <relrow>
    <relcell><topicref href="about_feechurr.md"/></relcell>
    <relcell>
      <topicref href="feechurr_install.md"/>
      <topicref href="feechurr_config.md"/>
    </relcell>
    <relcell>
      <topicref href="cmd_debug.md" linking="targetonly"/>
      <topicref href="cmd_report.md" linking="targetonly"/>
    </relcell>
  </relrow>

  <!-- more rows, if needed... -->
</reltable>
