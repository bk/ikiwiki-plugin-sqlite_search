# IkiWiki::Plugin::sqlite\_search

Search backend for IkiWiki based on SQLite FTS

## SYNOPSIS

This is a full text search module for IkiWiki which uses SQLite as a backend.
It requires the DBD::SQLite Perl module, but otherwise has very few
dependencies.

IkiWiki has an official search module based on Xapian, which is very fast and
efficient but may not be available on your system. Installing Xapian, along
with the omega CGI program, may be impractical because of the platform on
which your site is hosted, or perhaps because your control over the web server
is too limited. In such cases, the `sqlite_search` plugin is an acceptable
substitute.

## INSTALLATION

1. **Install the library.** Normally it goes into 
   `~/.ikiwiki/IkiWiki/Plugin/`, but you may prefer some other location in 
   your Perl path.

2. **Configure IkiWiki.** This involves editing your `*.setup` file. Under the 
   key `add_plugins:`, add a list item: `- sqlite_search`. (If there is a line 
   that reads `- search`, comment it out -- the official search plugin and 
   `sqlite_search` cannot both be active at the same time).

3. **Install templates.** The templates `search-result-form.tmpl` and
   `search-result.tmpl` must be copied to an appropriate location. This
   is normally in the `templates/` folder of your project. The templates
   may of course be modified if you like.

4. **Run ikiwiki -setup** on your `*.setup` file. This creates the text index 
   if needed and refreshes it otherwise.

## CAVEATS

- Pagination has not been implemented yet. The whole set of results is 
  displayed on one page.

- Although UTF-8 encoding is used by the backend, the summary and snippet
  extraction features pretty much assume a language using a Latin alphabet,
  although Cyrillic and Greek might be all right. Asian languages almost
  certainly will not work well.

- On a related note, the locale under which the `ikiwiki.cgi` program runs
  should use the UTF-8 character set -- at least if you have any non-ascii
  content which you want to be searcheable.

- This module is not suitable for big sites. A few hundred pages is fine, but 
  a few thousand may be a problem.

## AUTHOR AND VERSION

Author: Baldur Kristinsson, <https://github.com/bk>.

This is version 0.2, December 2014.

## COPYRIGHT AND LICENCE

This software is copyright (c) 2014 by Baldur Kristinsson.

This is free software with a dual Artistic/GPL license. The terms for using,
copying, distributing and modifying it are the same as for Perl 5.
