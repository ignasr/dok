partitioning
============

Using ``parted -a opt`` automaticaly aligns partitions. If possible, use it always instead of fdisk.

.. code-block:: none

   # parted -a optimal /dev/sda ["print free"]
   # print free
   # mkpart extended 47.8G 898G
   # mkpart logical 47.8G 590G

Check alignment with partition index, no output if OK:

.. code-block:: none

   # align-check opt 5
