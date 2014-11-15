kvm
===

solaris
-------

.. code-block:: none

   WARNING: /pci@0,0/pci1af4,1100@1,2 (uhci0): No SOF interrupts have been received
   , this USB UHCI host controller is unusable

This is harmless and can be safely ignored. Once the install is complete, we will disabled uhci by running rem_drv uhci in the server. 
