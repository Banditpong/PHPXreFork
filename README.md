Fork of PHPXref 0.7.1
======================

PHPXref 0.7.1 Original Instructions are below

PHPXref 0.7.1
=============

_© Gareth Watts <gareth@omnipotent.net> 2000-2007_

Contents
--------

*   [Synopsis](#synopsis)
*   [Quickstart](#quickstart)
*   [Documentating your scripts](#docs)
*   [Notes for Windows users](#windows)
*   [Miscellaneous](#misc)

Synopsis
--------

PHPXref parses a set of PHP files and extracts suitably formatted comments placed in the files to generate a cross-referenced set of HTML documentation that you can view using any web browser, with or without a web server.

### Features:

*   Provides an easy means of documenting your PHP scripts whilst you code.
*   Cross-references classes, functions, variables, constants, include() and require()'d files and SQL table usage.
*   Produces a complete class, function, variable, constant and (optionally) a database table list.
*   Generates plain HTML output that can be viewed with any web browser and downloaded onto the local machine for quick reference.
*   Generates a client-side quick-search search box for javascript-enabled browsers.
*   Pretty-prints PHP pages from your web browser.
*   Optionally compresses output files.

### Requirements:

*   Perl 5.6 or later.
*   A web browser - Having javascript enabled provides a nice search box, improves the navigation column and adds tooltip-style popups to classes and functions in the source view, but it's optional — the system is usable in Lynx, if not quite as feature-rich.
*   Some PHP files to cross reference.

That's it! No special / non-standard perl modules are required and the script is known to work fine under Linux, Windows and OS X and will probably work on other platforms as well.

You also don't need a web server - You can run the script locally and point your browser directly at the index.html file - In fact, this is the recommended way to use it as it makes for a very useful and fast programmer's tool.

Quickstart
----------

1.  Extract the PHPXref archive.
2.  Put a copy of your PHP code to cross reference into the source directory or edit phpxref.cfg and edit the SOURCE entry.
3.  Customize the phpxref.cfg file as you wish.
4.  Run phpxref.pl
5.  Load up the index.html file in the output directory in a browser.

Make sure the INCLUDEPATH setting in the configuration file is correct so that scripts that reference other scripts in the source directory find each other. Additionally, if you have require or include statements that use a constant or variable to specify a base directory, specify those in the configuration file too. Eg. if your code specifies:  

Require(TEMPLATE\_DIRECTORY . 'header.php');

you may want to set

TEMPLATE\_DIRECTORY=templates/

in the configuration file (be sure not to miss the trailing slash in the above example!).

Documenting your scripts
------------------------

As of version 0.3, PHPXref supports [PHPDocumentor](http://phpdocu.sourceforge.net/) style comments for documenting files, classes and functions (support for the old documentation format is retained but deprecated). PHPXref isn't intended to be a substitute for projects like phpdoc, but seems to compliment it fairly well.

An example function comment might look like..:

/\*\*
\* Authenticate a user using a username and password
\*
\* A longer description of the function might go here
\* and can span multiple lines.
\* @param string $username
\* @param string $password
\* @tables users, permissions
\* @author Gareth
\*/
function authuser($username,$password) {
    // ...
}
        

### Cross referencing database table references

PHPXref can cross reference database table usage in your scripts if you provide it with some hints about which tables you're using and where. This is needed as the parser doesn't currently know SQL. Additionally, if you use MySQL, you can have PHPXref go on to fetch the table descriptions directly from the database - Instructions for configuring this are in the config file. Note that you must have the Perl DBI modules installed to use this feature and the Windows .exe version doesn't include these modules. Thus to use this feature under Windows, you must use the .pl script with a full install of Perl.

Table hints for PHPXref can be provided either by specifying them as part of a file/class/function comment as shown above with the @tables tag.

Notes for Windows users
-----------------------

Version 0.3 of PHPXref contains some minor updates to help it run under Windows, but as I rarely use Windows I'm sure it has some issues remaining. If you wish to use PHPXref under Windows then you need to have a working installation of Perl. The easiest way to get this setup is to download the ActivePerl installer from [ActiveState](http://www.activestate.com/) and allow it to install into C:\\Perl. If you install it into another location you'll want to edit the phpxref.bat file before running it.

If you really don't want to install Perl, a copy of PHPXref compiled into a standalone executable using [TinyPerl](http://tinyperl.sourceforge.net/) is available on the [website](http://phpxref.sourceforge.net/).

Miscellaneous
-------------

### Copyright

PHPXref is © Gareth Watts and is licensed under the [GNU General Public License v2](COPYING)

### Contributions

*   Gottfried Szing <goofy@yasd.dhs.org>
*   Public domain icons from the [Apache web server](http://www.apache.org/)
*   Windows binary produced using [TinyPerl](http://tinyperl.sourceforge.net/)
*   Javascript explorer tree by [Softcomplex](http://www.softcomplex.com/products/tigra_menu_tree/)

Bug reports, patches and suggestions are welcome: Please suggest them via the [SourceForge project tracker](http://sourceforge.net/projects/phpxref/).
