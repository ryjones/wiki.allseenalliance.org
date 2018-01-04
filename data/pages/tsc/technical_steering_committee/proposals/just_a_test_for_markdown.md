# A Page to Test Markdown Extra Support and HTML block Support in our AllSeen Wiki

This page is to test if the DokuWiki Markdownextra plug-in is installed for this Wiki.  This page also includes a test for HTML support in this wiki.  Since AllSeen Alliance has adopted Markdown as the official documentation creation format - it seemed good to enable this support.  The support for HTML content would also be desirable, given the large number of contributors who are HTML savvy. This is a simple Dokuwiki configuration setting to enable - no plug in needed.

The plug-in is easy to use and lets any of our developers who write documentation in Markdown directly copy content into a new Dokuwiki page.

The plug-in is available from the Dokuwiki plug-ins pages at [https://www.dokuwiki.org/plugin:markdownextra](https///www.dokuwiki.org/plugin/markdownextra)

You can see by the lack of styling in the rest of this page that neither is currently supported by this wiki.

`<markdown>`

# Heres a Heading 1

Some body text here. Mary had a little lamb, fleece was white as snow.  Everywhere the child went the lamb was sure to go.  He followed her to school one day, broke the teacher's rule. What fun did they have that day at school.

## And a Heading 2

Here's a numbered list with nested bullets

1. item 1
2. item 2

	* bullet 1
	* bullet 2
	* bullet 3
3. item 3

### And a heading 3

## Back to a heading 2

`</markdown>`

The following section tests if HTML tag supported in enabled in the DokuWiki configuration settings of the site.

`<html>`

`<h1 id="heresaheading1">`Heres a Heading 1`</h1>`

`<p>`Some body text here. Mary had a little lamb, its fleece was white as snow. Everywhere the child went the lamb was sure to go. Followed her to school one day, broke the teacher&#8217;s rule. What fun they had that day at school.`</p>`

`<h2 id="andaheading2">`And a Heading 2`</h2>`

`<p>`Here&#8217;s a numbered list with nested bullets`</p>`

`<ol>`
`<li>`item 1`</li>`
`<li>`item 2

`<ul>`
`<li>`bullet 1`</li>`
`<li>`bullet 2`</li>`
`<li>`bullet 3`</li>`
`</ul>``</li>`
`<li>`item 3`</li>`
`</ol>`

`<h3 id="andaheading3">`And a heading 3`</h3>`

`<h2 id="backtoaheading2">`Back to a heading 2`</h2>`

`</html>`
