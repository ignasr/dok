zfs
===

.. code-block:: none

    dkms status

links
-----

Naudingi patarimai is Arch: https://wiki.archlinux.org/index.php/ZFS

cheat sheets
------------

http://www.datadisk.co.uk/html_docs/sun/sun_zfs_cs.htm

zfs on linux
------------

.. code-block:: none

    zfs set sharenfs="rw=192.168.1.1/24,ro=192.168.2.1/24,no_root_squash"

Does not work with different option for different hosts:

.. code-block:: none

    zfs set sharenfs="rw=192.168.1.1/24,async,ro=192.168.2.1/24,sync" rpool/exports

