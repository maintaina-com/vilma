==============================
||  INSTALLING Vilma 0.1  ||
==============================

* PLEASE SEE IMPORTANT NOTE in the README file about Vilma's status
  before you try to install it and are disappointed.

This document contains instructions for installing the Vilma virtual mail
domain management application.

For information on the capabilities and features of Vilma, see the
file README in the top-level directory of the Vilma distribution.


OBTAINING VILMA
-----------------

Vilma can be obtained from the Horde website and FTP server, at

   http://www.horde.org/apps/vilma
   ftp://ftp.horde.org/pub/vilma/

Bleeding-edge development versions of Vilma are available via CVS; see
the file doc/HACKING in the Horde distribution for information on
accessing the Horde CVS repository.


PREREQUISITES
-------------

To function properly, Vilma **requires** the following:

  1. A working Horde installation.

     Vilma runs within the Horde Application Framework, a set of
     common tools for Web applications written in PHP. You must
     install Horde before installing Vilma.

     The Horde Framework can be obtained from the Horde website and
     FTP server, at

        http://www.horde.org/apps/horde
        ftp://ftp.horde.org/pub/horde/

     Many of Vilma's prerequisites are also Horde prerequisites.
     Be sure to have completed all of the steps in the INSTALL
     file for the Horde Framework before installing Vilma.

  2. SQL support in PHP.

     Vilma store its data in an SQL database. Build PHP with whichever
     SQL driver you require; see the Horde INSTALL file for details.


INSTALLING VILMA
------------------

Vilma is written in PHP, and must be installed in a web-accessible
directory. The precise location of this directory will differ from
system to system. Conventionally, Vilma is installed directly underneath
Horde in the webserver's document tree.

Since Vilma is written in PHP, there is no compilation necessary;
simply expand the distribution where you want it to reside and rename
the root directory of the distribution to whatever you wish to appear
in the URL. For example, with the Apache webserver's default document
root of '/usr/local/apache/htdocs', you would type:

   cd /usr/local/apache/htdocs/horde
   tar zxvf /path/to/vilma-0.1.tar.gz
   mv vilma-0.1 vilma

and would then find Vilma at the URL

   http://your-server/horde/vilma/


CONFIGURING VILMA
-------------------

1. Configuring Horde for Vilma

   a. Register the application

      In horde/config/registry.php, find the applications['vilma'] stanza.
      The default settings here should be okay, but you can change
      them if desired.  If you have changed the location of Vilma relative
      to Horde, either in the URL, in the filesystem or both, you must
      update the 'fileroot' and 'webroot' settings to their correct
      values.

2. Creating the database table

   The specific steps to create the Vilma database table depend
   on which database you've chosen to use.

   First, look in scripts/drivers/ to see if a script already
   exists for your database type. If so, you should be
   able to simply execute that script as superuser in your
   database. (Note that executing the script as the "horde" user will
   probably fail when granting privileges.)

   If such a script does not exist, you'll need to build your own, using
   the file vilma.sql as a starting point. If you need
   assistance in creating databases, you may wish to let us know on
   the Vilma mailing list.

3. Configuring Vilma.

   Documentation on the format and purpose of the configuration files in the
   ``config/`` directory can be found in each file.  You may edit these files
   if you wish to customize Vilma's appearance and behavior.  The defaults
   will be correct for most sites.

   You must login to Horde as a Horde Administrator to finish the
   configuring of Vilma.  Use the Horde "Administration" menu item to get
   to the Administration page, and then click on the "Configuration"
   icon to get the Configuration page.  Select "Tasks" from the selection
   list of applications, and click on the "Configure" button.  Fill in or
   change any configuration values as needed.  When done click on "Generate
   Tasks Configuration" to generate the conf.php file.  If your web server
   doesn't have write permissions to the Vilma configuration directory or
   file, it will not be able to write the file.  In this case, cut and
   paste the returned configuration information into the file
   vilma/config/conf.php.

   Note for international users:  Vilma uses GNU gettext to provide local
   translations of text displayed by applications; the translations are
   found in the po/ directory.  If a translation is not yet available
   for your locale (and you wish to create one), or if you're having
   trouble using a provided translation, please see the horde/doc/TRANSLATIONS
   file for instructions.

4. Testing Vilma

   Use Vilma to create, modify, and delete forms. Test at
   least the following:

     - Creating a form
     - Modifying a form
     - Viewing and submitting a form
     - Deleting a form


SAMPLE USAGE
------------

Vilma can be embedded internally within Horde in any application which
supports the Horde Blocks API.

Otherwise Vilma can be called from any web page with the following simple
php code:

   <?php
   $form_id = 2;
   include <pathtovilma> . '/display.php';
   ?>


OBTAINING SUPPORT
-----------------

If you encounter problems with Vilma, help is available!

The Horde Frequently Asked Questions List (FAQ), available on the Web
at

  http://wiki.horde.org/FAQ

The Horde Project runs a number of mailing lists, for individual
applications and for issues relating to the project as a whole.
Information, archives, and subscription information can be found at

  http://www.horde.org/community/mail

Lastly, Horde developers, contributors and users may also be found on IRC,
on the channel #horde on the Freenode Network (irc.freenode.net).

Please keep in mind that Vilma is free software written by volunteers.
For information on reasonable support expectations, please read

  http://www.horde.org/community/support

Thanks for using Vilma!

The Vilma team
