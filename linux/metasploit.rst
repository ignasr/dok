metasploit
==========

install 
-------

Install rbenv (linux/rbenv.md) to /root and the latest ruby 1.9.

.. code-block:: none

   $ mkdir /opt/metasploit 
   $ cd /opt/metasploit <- set local rbenv
   $ git clone https://github.com/rapid7/metasploit-framework.git msf

Then http://www.phocean.net/2014/02/23/metasploit-on-fedora-20.html

run
---

.. code-block:: none

   # ./msfconsole

commands
--------

global
``````

.. code-block:: none

   search
   search name:mysql
   search path:scada
   search platform:aix
   search type:post
   search cve:2011 author:jduck platform:linux
   setg
   save
   show
   show auxiliary

plugin
``````

.. code-block:: none

   info
   show options
   run
   jobs

scans
-----

ssdp
````

.. code-block:: none

   use auxiliary/scanner/upnp/ssdp_amp  :: amp?
   use auxiliary/scanner/upnp/ssdp_msearch  :: info

   set RHOSTS 192.168.0.0/24
   run

