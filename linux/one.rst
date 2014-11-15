opennebulla
===========

Nauodjimas
----------

onevnet 
```````

.. code-block:: none

   # onevnet list

sunstone
````````

http://opennebula.org/documentation:archives:rel4.0:sunstone

The default password for the oneadmin user (which can be changed by doing oneuser passwd oneadmin <new_password>), can be found in ~/.one/one_auth which is generated randomly on every installation.

one market
``````````

.. code-block:: none

   # onemarket list --server http://marketplace.c12g.com

Instaliavimas
-------------

Irasius servisus, juos isjungti.

Tinklas
```````

https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/s2-networkscripts-interfaces_network-bridge.html

.. code-block:: none

   ifcfg-eth0:
   DEVICE="eth0"
   TYPE="Ethernet"
   BOOTPROTO="none"
   ONBOOT="yes"
   NM_CONTROLLED="no"
   BRIDGE=onebr0
   gali reikti HWADDR
   
   ifcfg-onebr0:
   DEVICE="onebr0"
   TYPE="Bridge"
   IPADDR="10.4.1.108"
   NETMASK="255.255.255.0"
   ONBOOT="yes"
   BOOTPROTO="none"
   GATEWAY="10.4.1.1"
   IPV6INIT="no"
   NM_CONTROLLED="no"

add host
````````

Hostas turi galeti useriu oneadmin prisijungti ir prie saves ir prie kitu.

Gali tekti pataisyti eilute oned.conf:

.. code-block:: none

   SCRIPTS_REMOTE_DIR=/var/lib/one/remotes
   
   onehost create localhost -i im_kvm -v vmm_kvm -n fw
