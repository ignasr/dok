ubuntu
======

Disable a service
-----------------

.. code-block:: none

   $ sudo invoke-rc.d apparmor stop
   $ sudo invoke-rc.d apparmor teardown
   $ sudo update-rc.d -f apparmor remove
