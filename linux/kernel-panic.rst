kernel panic
============

Causing a kernel panic on CentOS6:

.. code-block:: none

   # echo c > /proc/sysrq-trigger

May be needed:

    echo 1 > /proc/sys/kernel/sysrq


configuring kdump on CentOS6
----------------------------

https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/ch-kdump.html

.. code-block:: none

   # yum install kexec-tools

Add to '/boot/grub/grub.conf' kernel line:

.. code-block:: none

   crashkernel=auto

if host has more than 2GB RAM, or 

.. code-block:: none

   crashkernel=128M

if host has less than that.

Saving place is configurable, default is '/var/crash/'.

.. code-block:: none

   # chkconfig kdump on
   # reboot

analyzing crash dump with crash
-------------------------------

installing kernel-debuginfo
---------------------------

http://serverfault.com/questions/527525/centos-server-rebooted-unexpectedly-and-im-unable-to-process-crash-file-what-a/527553#527553


.. code-block:: none

   # yum clean all
   # yum install crash
   # versija=`uname -r`

Pries 'y' patikrinam ar ta versija ir ar ne koks nors centos-plus paketas:

.. code-block:: none

   # yum --enablerepo=debug install kernel-debuginfo-$versija

using crash
-----------

Kernel cersions must be the same:

.. code-block:: none

   # crash /var/crash/timestamp/vmcore /usr/lib/debug/lib/modules/kernel/vmlinux

   > help [cmd]
   > log
   > bt
   > ps
   > vm [pid]
   > files [pid]

kdump.conf(5) — a manual page for the /etc/kdump.conf configuration file containing the full documentation of available options.

makedumpfile(8) — a manual page for the makedumpfile core collector.

kexec(8) — a manual page for kexec.

crash(8) — a manual page for the crash utility.

/usr/share/doc/kexec-tools-version/kexec-kdump-howto.txt — an overview of the kdump and kexec installation and usage.
