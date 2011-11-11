html2markdown for PHP
=====================

An HTML-to-markdown conversion tool for PHP by Nick Cernis  
[@nickcernis](http://twitter.com/nickcernis)  |  http://modnerd.com

Version 1.0.1  
Requires PHP 5  
Licensed under The MIT license: http://www.opensource.org/licenses/mit-license.php

###Live demo
A live demo is available at http://modnerd.com/html2markdown/

###Instructions

Include html2markdown.php:
	
	require_once( dirname( __FILE__) . '/html2markdown.php' );
       
Call html2markdown() on your valid, slash-stripped HTML code:

    $markdown = html2markdown($html);
    
The `$markdown` string now contains the markdowned version of your HTML.

The included `demo.php` file contains an HTML->markdown conversion form for testing.

###Limitations

- Chokes on malformed HTML. i.e. unclosed tags. Am considering a cleanup function to check for simple errors with an off switch for projects that perform their own reformatting, like WordPress. At present, you must nest `<code>` blocks inside `<p>` or `<pre>`, for example.
- Markdown Extra, MultiMarkdown and other variants aren't supported; just Markdown.

###Bugs

- Nested lists and lists with multiple paragraphs aren't converted correctly.
- Lists inside blockquotes aren't converted correctly.

###Style notes

- SETEX (underlined) headers are the default for H1 and H2. Change the HTML2MD_HEADER_STYLE constant to "ATX" if you want `# H1` and `## H2` style tags instead.
- Reference-style labels (with src and href links in the footnotes) are not used. Links and images are all referenced inline.
- Blockquotes aren't line wrapped (makes them easier to edit).

###Architecture notes

html2markdown is about 450 lines. It's a single file with no dependencies. It uses native DOM manipulation libraries (DOMDocument), not regex voodoo, 
to convert code. I'd appreciate your help with any bug fixes and improvements.

###Contributors

My thanks to [unlight](https://github.com/unlight) and [iamthes](https://github.com/iamthes) for their contributions.

###How it works
html2markdown creates a DOM tree from the supplied HTML, walks through the tree, and converts each node to a text node, starting from the most deeply nested node and working inwards towards the root node.


###TO-DO

- Support for nested lists and lists inside blockquotes.

###Trying to convert Markdown to HTML?

Use [PHP Markdown](http://michelf.com/projects/php-markdown/) from Michel Fortin.

