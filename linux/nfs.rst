nfs
===

configuring nfs server on centos6
---------------------------------

.. code-block:: none

   yum install nfs-utils
   
   vim /etc/sysconfig/nfs (PAPILDYTI)
   ---
   > MOUNTD_NFS_V2="no"
   > RQUOTAD_PORT=875
   > LOCKD_TCPPORT=32803
   > LOCKD_UDPPORT=32769
   > MOUNTD_PORT=892
   > STATD_PORT=662
   > STATD_OUTGOING_PORT=2020
   ---

   mkdir -p /export/public
   
   vim /etc/exports
   ---
   /export/public *(rw,no_subtree_check,insecure,no_root_squash,no_all_squash)
   ---
   
   vim /etc/sysconfig/iptables
   ---
   -A INPUT -m multiport -p tcp --dport 111,662,875,892,2049,32803 -j ACCEPT
   -A INPUT -m multiport -p udp --dport 111,662,875,892,2049,32769 -j ACCEPT
   ---
   
   service iptables restart
   chkconfig nfs on
   service rpcbind start
   service nfslock  start
   service nfs start
    
Jei reikia reeksportuoti:

.. code-block:: none

   # exportfs -rv
    
Klientas:

.. code-block:: none

   # yum install nfs-utils
   # 
   # showmount -e 10.10.40.210
   # 
   # mkdir /mnt/public
   # 
   # vim /etc/fstab
   # ---
   # 10.10.40.210:/export/public /mnt/public nfs defaults        0 0
   # 10.10.40.210:/export/store  /mnt/store  nfs vers=3,nolock,rw,acl,tcp,hard,intr,rsize=32768,wsize=32768 0 0
   # ---
   # 
   # mount -a

Useriai NFS serveryje ir kliente turi buti vienodu vardu bei UID GID. 
Todel userius pirmiausia kurti severyje.

Apie GID/UID problemas http://dfusion.com.au/wiki/tiki-index.php?page=Why+NFSv4+UID+mapping+breaks+with+AUTH_UNIX

troubleshooting
---------------

Clear idmapd cache
``````````````````
    
.. code-block:: none

   # nfsidmap -c

Remove stale handles
````````````````````

Login as root. Issue the commands:

.. code-block:: none

   # service netfs stop
   # service network restart
   # service netfs start


