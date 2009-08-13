Introduction
============

This tool provides an easy way for users to retrieve their SLCS certificates from a SWITCH SLCS server.

Usage
-----

Usage::

  $ slick-init --help
  Usage: slick-init [options] [idp]
  
  Options:
    -h, --help            show this help message and exit
    -d DIR, --storedir=DIR
                          the directory to store the certificate/key and
                          config file
    -i IDP, --idp=IDP     unique ID of the IdP used to log in
    -s SLCS, --slcs=SLCS  location of SLCS server (if not specified, use
                          SLCS_SERVER system variable or settings from
                          [storedir]/slcs-client.properties
    -f SEARCHSTRING, --find=SEARCHSTRING
                          find IdP(s) whose name or unique ID contain a
                          specified string
    -k, --key             prompt for key-passphrase (use Shibboleth password
                          by default)
    -l, --list            list all available IdP(s)
    -w, --write           write the arguments specified on the command line to
                          a config file
    -v, --verbose         print status messages to stdout



Config File
-----------

The contents of a simple config file::

  $ cat ~/slcs-client.properties
  [slcs]
  idp = VPAC
  url = https://slcs1.arcs.org.au/SLCS/login

Install
=======

Ubuntu
------
::

  apt-get install python-setuptools python-m2crypto

  easy_install --index-url http://code.arcs.org.au/pypi/ slick

Centos5
-------

::

  $ yum install python-setuptools swig openssl-devel gcc subversion

  $ sudo easy_install virtualenv
  $ virtualenv slick
  $ cd slick

Once we activate the virtual envionment the PATH will be changed so that 
files within slick/bin/ will take precidence.

::

  $ . ./bin/activate
  (slick)$ svn co http://svn.osafoundation.org/m2crypto/tags/0.19.1/ m2crypto
  (slick)$ cd m2crypto
  (slick)$ python setup.py build_ext -I/usr/include/openssl install
  (slick)$ easy_install slick
  (slick)$ deactivate

Once the virtulenv is deactivated you can still run the command directly

::

  ./bin/slick-init
