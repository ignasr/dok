btrfs
=====

Use ZFS on Linux instead!

http://www.funtoo.org/BTRFS_Fun

Install
-------

.. code-block:: none

   # yum install btrfs-progs

Jeigu kuriam is vieno disko:

.. code-block:: none

   # mkfs.btrfs -m single /dev/sdb
   # mount -o compress=zlib

compress=zlib - Better compression ratio. It is the default and safe for olders kernels.
compress=lzo - Faster compressions, newer kernels.


Info
----

.. code-block:: none

   # btrfs filesystem show
   # btrfs filesystem df


Test A
------

10x 300mb

be comp


====    =========
real    1m57.278s
user    0m0.044s
sys     0m5.639s
====    =========

Jei testuojame su loop, ir norime daryti masyva is keliu failu, reikia daryti kitaip:

Create and mount a filesystem made of several disk images

.. code-block:: none

   # mkfs.btrfs img0 img1 img2
   # losetup /dev/loop0 img0
   # losetup /dev/loop1 img1
   # losetup /dev/loop2 img2
   # mount /dev/loop0 /mnt/btrfs
