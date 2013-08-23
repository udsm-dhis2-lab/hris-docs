.. contribution:

Contribute to Software Source Codes
===================================

Code
****

	In case you will notice inconsistencies in the HRIS System please folow the instructions below.

Reporting a Bug
---------------

	Whenever you find a bug in HRIS, we kindly ask you to report it. It helps us make a better HRIS.	

Reporting a Security Issue
--------------------------

	If you find a security issue in HRIS please do not reveal the issue to the public, report it to the HRIS-Project Team via 		   		`John F. Mukulu <mailto:john.f.mukulu@gmail.com>`_

	For each report, we first try to confirm the vulnerability. When it is confirmed, the Team works on a solution following these steps:

		1. Send an acknowledgement to the reporter;

		2. Work on a patch;

		3. Write a post describing the vulnerability, the possible exploits, and how to patch/upgrade affected applications;

		4. Apply the patch to all maintained versions of HRIS;

		5. Inform the reporter of the Security Issue that the Issue has been resolved:
		
	.. Note::
           While we are working on a patch, please do not reveal the issue publicly.
		


Contribute to Documentation
===========================

	Documentation is as important as code. It follows the exact same principles: DRY, tests, 
        ease of maintenance, extensibility, optimization,
        and refactoring just to name a few. And ofcourse documentation has bugs, typos, 
        hard to read tutorials, and more. Human resource for health information system 3.0. 
        source code and documentation are hosted on github:
        
            * `Hris Website - https://github.com/hrisproject/hris <https://github.com/hrisproject/hris>`_
            * `Hris Documentation - https://github.com/hrisproject/hris-docs <https://github.com/hrisproject/hris-docs>`_
            
            If you want to submit a patch, fork the official repository on GitHub and then clone your fork::
            
            $ git clone git://github.com/YOURUSERNAME/hris-docs.git
            
            Make your changes into the documentation, when you're done create a pull request on github.
            
            GitHub covers the topic of  `pull request <https://help.github.com/articles/using-pull-requests>`_ in detail.
            
Contributing
************

	Before contributing, you need to become familiar with the markup language used by the documentation.

        HRIS Documentation uses reStructuredText as its markup language and Sphinx for building the output(HTML,PDF, etc...).

reStructuredText
****************

        reStructuredText "is an easy-to-read, what-you-see-is-what-you-get plaintext markup syntax and parser system".
        
        If you're familiar with Markdown, be careful as things are sometimes very similar but different
        
            * Lists start at the beggining of a line(no indentation)
            * Inline code blocks use double-ticks(like this)
            
        Quick overview on reStructuredText can be found on `sphnix website <http://sphinx-doc.org/rest.html>`_
        A more detailed documentation can be found at `reStructuredText website <http://docutils.sourceforge.net/rst.html>`_
        
Sphinx
******

    Sphnix is a build system that adds some nice tools to create documentation from reStructuredText documents. 
    As such, it adds new directives and interpreted text roles to standard reST `markup <http://sphinx-doc.org/markup/>`_.

    Quick overview on setting your sphinx up for documentation can be found from `matplotlib website <http://matplotlib.org/sampledoc/>`_,
    a more detailed documentation can be found at `sphnix website <http://sphinx-doc.org/rest.html>`_
    
Testing Documentation
*********************

    To test documentation before a commit:
    
        * Install Sphinx;
        * Run the Sphinx quick setup;
        * Install the Sphinx extensions (see below);
        * Run make html and view the generated HTML in the build directory.
        
Installing the Sphinx extensions
********************************

    Download the extension from the source repository Copy the sensio directory to the _exts folder under your source 
    folder (where conf.py is located) Add the following to the conf.py file::
    
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
        
Generating PDF Using rest2pdf
*****************************

    st2pdf user manual (you can simply refer to the "Sphinx" chapter)
    https://docs.google.com/viewer?url=http%3A%2F%2Fsphinx.pocoo.org%2Fsphinx-rst2pdf.pdf
    
    Install rst2pdf
     
        - use your package manager (or)
        - pip install rst2pdf (or)
        - easy_install rst2pdf
        
     Add rst2pdf to the list of extensions in conf.py::
     
        extensions = ['rst2pdf.pdfbuilder']
     
     This list will be empty if you accepted the defaults when the project was setup. If not, 
     just append 'rst2pdf.pdfbuilder' to the list.
     
     Add a pdf_documents variable to conf.py::
     
        pdf_documents = [('index', u'rst2pdf', u'Sample rst2pdf doc', u'Your Name'),]
   
        # index - master document
        # rst2pdf - name of the generated pdf
        # Sample rst2pdf doc - title of the pdf
        # Your Name - author name in the pdf
        
     For all supported options, please check the `manual <http://lateral.netmanagers.com.ar/static/manual.pdf>`_ 
     
     Generate pdf::
     
        sphinx-build -b pdf source build/pdf

     The generated pdf will be in the build/pdf directory. 
Financing the Open Source Project
=================================









