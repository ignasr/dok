SELinux
=======

.. code-block:: none

   semodule -DB  : enable full logging
   semanage fcontext -a -t virt_etc_t '/shared(/.*)?'
   restorecon -r /shared


