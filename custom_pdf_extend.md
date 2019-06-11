---
ID: custom_pdf_extend
author: Larry Kollar
publisher: Oje Media
---

# Extending the Simple PDF Plugin

Now that you have a basic plugin, we’ll extend it a little more.

In this example, we:

* make the headers more flexible, and add chapter number support
* format blockquotes (`lq`) to look like actual blockquotes
  (DITA-OT 3.2 corrects this issue)
* even out the spacing in list items

You can edit the existing, simple plugin in-place without having to install again.

1.  Add the following attribute sets to the bottom of `cfg/fo/attrs/custom.xml`
    (above the final `</xsl:stylesheet>` line).
    This sets up blockquote and list item formatting.
    ```xml
    <!-- blockquotes (not required for DITA-OT 3.2 and newer)-->
    <xsl:attribute-set name="lq" use-attribute-sets="common.block">
      <xsl:attribute name="margin-left">0.25in</xsl:attribute>
      <xsl:attribute name="margin-right">0.25in</xsl:attribute>
    </xsl:attribute-set>

    <xsl:attribute-set name="lq_simple" use-attribute-sets="common.block lq">
    </xsl:attribute-set>

    <!-- list items -->
    <xsl:attribute-set name="ul.li">
        <xsl:attribute name="space-after">0.6em</xsl:attribute>
        <xsl:attribute name="space-before">0.6em</xsl:attribute>
        <xsl:attribute name="relative-align">baseline</xsl:attribute>
    </xsl:attribute-set>

    <xsl:attribute-set name="ol.li">
        <xsl:attribute name="space-after">0.6em</xsl:attribute>
        <xsl:attribute name="space-before">0.6em</xsl:attribute>
        <xsl:attribute name="relative-align">baseline</xsl:attribute>
    </xsl:attribute-set>
    ```

2.  Edit `cfg/common/vars/en.xml`, modifying the body headers and adding new variables:
    ```xml
    <variable id="Body first header"/>
    <variable id="Body odd header"><param ref-name="pagenum"/></variable>
    <variable id="Body even header"><param ref-name="pagenum"/></variable>
    <variable id="Body odd header inner"><param ref-name="heading"/></variable>
    <variable id="Body even header inner">Chapter <param ref-name="number"/></variable>
    ```
    You can change other variables in `en.xml` as well.

3.  Edit `cfg/fo/xsl/custom.xsl` and add the following template:
    ```xml
    <!-- get header variables -->
    <xsl:template name="getHeaderVars">
      <xsl:param name="arg"/>

      <xsl:call-template name="getVariable">
          <xsl:with-param name="id" select="$arg"/>
          <xsl:with-param name="params">
              <prodname>
                  <xsl:value-of select="$productName"/>
              </prodname>
              <heading>
                  <fo:inline>
                      <fo:retrieve-marker
                        retrieve-class-name="current-header"/>
                  </fo:inline>
              </heading>
              <number>
                <fo:inline>
                    <xsl:apply-templates
                      select="key('map-id', @id)[1]"
                      mode="topicTitleNumber"/>
                </fo:inline>
              </number>
              <pagenum>
                  <fo:inline
                    xsl:use-attribute-sets="__body__odd__header__pagenum">
                      <fo:page-number/>
                  </fo:inline>
              </pagenum>
          </xsl:with-param>
      </xsl:call-template>
    </xsl:template>
    ```
    This breaks out the header variable code, making other header processing more readable,
    and adds a parameter to fetch the current chapter number (missing from the default processing).

4.  Modify the templates below:
    ```xml
    <xsl:template name="insertBodyOddHeader">
      <fo:static-content flow-name="odd-body-header">
          <fo:block xsl:use-attribute-sets="__body__odd__header">
            <fo:inline xsl:use-attribute-sets="__body__odd__header__heading">
              <xsl:call-template name="getHeaderVars">
                <xsl:with-param name="arg" select="'Body odd header inner'"/>
              </xsl:call-template>
            </fo:inline>
            <fo:leader leader-pattern="space"/>
            <fo:inline xsl:use-attribute-sets="__body__odd__header__heading">
              <xsl:call-template name="getHeaderVars">
                <xsl:with-param name="arg" select="'Body odd header'"/>
              </xsl:call-template>
            </fo:inline>
          </fo:block>
      </fo:static-content>
    </xsl:template>

    <xsl:template name="insertBodyEvenHeader">
        <fo:static-content flow-name="even-body-header">
            <fo:block xsl:use-attribute-sets="__body__even__header">
              <fo:inline
                xsl:use-attribute-sets="__body__even__header__heading">
                <xsl:call-template name="getHeaderVars">
                  <xsl:with-param name="arg" select="'Body even header'"/>
                </xsl:call-template>
              </fo:inline>
              <fo:leader leader-pattern="space"/>
              <fo:inline
                xsl:use-attribute-sets="__body__even__header__heading">
                <xsl:call-template name="getHeaderVars">
                  <xsl:with-param name="arg"
                    select="'Body even header inner'"/>
                </xsl:call-template>
              </fo:inline>
            </fo:block>
        </fo:static-content>
    </xsl:template>

    <xsl:template name="insertBodyFirstHeader">
        <fo:static-content flow-name="first-body-header">
            <fo:block xsl:use-attribute-sets="__body__first__header">
            </fo:block>
        </fo:static-content>
    </xsl:template>

    <!-- duplicate even header -->
    <xsl:template name="insertBodyLastHeader">
        <fo:static-content flow-name="last-body-header">
          <fo:block xsl:use-attribute-sets="__body__even__header">
            <fo:inline
              xsl:use-attribute-sets="__body__even__header__heading">
              <xsl:call-template name="getHeaderVars">
                <xsl:with-param name="arg" select="'Body even header'"/>
              </xsl:call-template>
            </fo:inline>
            <fo:leader leader-pattern="space"/>
            <fo:inline
              xsl:use-attribute-sets="__body__even__header__heading">
              <xsl:call-template name="getHeaderVars">
                <xsl:with-param name="arg" select="'Body even header inner'"/>
              </xsl:call-template>
            </fo:inline>
          </fo:block>
        </fo:static-content>
    </xsl:template>
    ```
    These templates make use of the chapter number we added in step 2,
    and eliminate blank headers when the last page of a chapter is even.

5.  If you made the modifications outside the plugin,
    copy the plugin directory to `plugins` in your DITA-OT directory.
    You do not need to run `dita --install`.
