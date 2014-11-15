luks
====

installing
----------

.. code-block:: none

   # yum install cryptsetup-luks

Removes all data:

.. code-block:: none

   # cryptsetup -y -v luksFormat /dev/xvdc

   # cryptsetup luksOpen /dev/xvdc backup2
   # ls -l /dev/mapper/backup2 
   # cryptsetup -v status

LUKS headers:

.. code-block:: none

   # cryptsetup luksDump /dev/xvdc


formatting
----------

Zero to hide usage patterns:

.. code-block:: none

   # pv -tpreb /dev/zero | dd of=/dev/mapper/backup2 bs=128M
   # kill -USR1 PID

   # mkfs.ext4 /dev/mapper/backup2

   # mkdir /backup2
   # mount /dev/mapper/backup2 /backup2


using
-----

Umount:

.. code-block:: none

   # umount /backup2
   # cryptsetup luksClose backup2

Mount:

.. code-block:: none

   # cryptsetup luksOpen /dev/xvdc backup2
   # mount /dev/mapper/backup2 /backup2

sources
-------

http://www.cyberciti.biz/hardware/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/
