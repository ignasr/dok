rbenv
=====

https://github.com/sstephenson/rbenv

info
----

``rbenv version`` parodyti dabartine nustatyta versija.

``rbenv versions`` parodyti instaliuotas versijas.

``rbenv global`` parodyti globalia versija.

``rbenv local`` parodyti lokalia versija.

upgrade
-------

.. code-block:: none

   $ cd ~/.rbenv
   $ git pull

To use a specific release of rbenv, check out the corresponding tag:

.. code-block:: none

   $ cd ~/.rbenv
   $ git fetch
   $ git checkout v0.3.0

install
-------

Verisiju saraso atnaujinimui reikia ruby-build upgrade (zemiau).

Perziurime esamas ruby versijas:

.. code-block:: none

   $ rbenv install --list

Instaliuojame reikalinga ruby versija (raikalingas ruby-build pluginas):

.. code-block:: none

   $ rbenv install 1.9.3-p448
   $ rbenv global 1.9.3-p448
   $ rbenv rehash


ruby-build
==========

upgrade
-------

.. code-block:: none

   $ cd .rbenv/plugins/ruby-build/
   $ git pull

