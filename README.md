HRIS Documentation
-----------------------------------------------------------

This is documentation for [Human Resource Information System](http://github.com/hrisproject/hris)
This documentation is rendered online at https://hris.readthedocs.org/

HRIS Documentation is licensed under GNU General Public Licence, either version 2
of the licence or at your option any later version.

##Contributing
---------------
Documentation is as important as code. It follows the exact same principles:
DRY, tests, ease of maintenance, extensibility, optimization, and refactoring
just to name a few. And ofcourse documentation has bugs, typos, hard to read 
tutorials, and more. 
Human resource for health information system 3.0. source code and documentation
are hosted on github:
* [Hris Website - https://github.com/hrisproject/hris ](https://github.com/hrisproject/hris)
* [Hris Documentation - https://github.com/hrisproject/hris-docs ](https://github.com/hrisproject/hris-docs)

If you want to submit a patch, fork the official repository on GitHub and then clone your fork:

	$ git clone git://github.com/YOURUSERNAME/hris-docs.git
	
Make your changes into the documentation, when you're done create a pull request
on github.

GitHub covers the topic of [pull requests](https://help.github.com/articles/using-pull-requests) in detail.

##We love contributors!
----------------------
Before contributing you need to be familiar with the markup language used by
the documentation.

HRIS Documentation uses reStructuredText as its markup language and Sphinx for
building the output(HTML,PDF, etc...).

###reStructuredText
--------------------
reStructuredText "is an easy-to-read, what-you-see-is-what-you-get plaintext markup syntax
and parser system".

If you're familiar with Markdown, be careful as things are sometimes very similar but different:
* Lists start at the beggining of a line(no indentation)
* Inline code blocks use double-ticks(``like this``)

Quick overview on reStructuredText can be found on [sphnix website](http://sphinx-doc.org/rest.html),
A more detailed documentation can be found at [reStructuredText website](http://docutils.sourceforge.net/rst.html)


###Sphinx
-----------
Sphnix is a build system that adds some nice tools to create documentation from
reStructuredText documents. As such, it adds new directives and interpreted text roles
to standard reST [markup](http://sphinx-doc.org/markup/).

Quick overview on setting your sphinx up for documentation can be found from 
[matplotlib website](http://matplotlib.org/sampledoc/), a more detailed documentation
can be found at [sphinx website](http://sphinx-doc.org/) 

###Testing Documentation
-------------------------
To test documentation before a commit:
* Install Sphinx;
* Run the Sphinx quick setup;
* Install the Sphinx extensions (see below);
* Run make html and view the generated HTML in the build directory.

###Installing the Sphinx extensions
------------------------------------
Download the extension from the source repository
Copy the sensio directory to the _exts folder under your source folder (where conf.py is located)
Add the following to the conf.py file:

	# ...
	sys.path.append(os.path.abspath('_exts'))

	# adding PhpLexer
	from sphinx.highlighting import lexers
	from pygments.lexers.web import PhpLexer

	# ...
	# add the extensions to the list of extensions
	extensions = [..., 'sensio.sphinx.refinclude', 'sensio.sphinx.configurationblock', 'sensio.sphinx.phpcode']

	# enable highlighting for PHP code not between ``<?php ... ?>`` by default
	lexers['php'] = PhpLexer(startinline=True)
	lexers['php-annotations'] = PhpLexer(startinline=True)

	# use PHP as the primary domain
	primary_domain = 'php'
