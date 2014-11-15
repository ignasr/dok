multicast
=========

bridge config
-------------

There are bugs in kernel when forwarding non 224.0.0.* multicast traffic through bridges, so disable snooping:

.. code-block:: none

   host# echo 0 > /sys/devices/virtual/net/br0/bridge/multicast_snooping

http://troglobit.com/blog/2013/07/09/multicast-howto/

Then to make it persistent... `/etc/sysconfig/network-scripts/ifup-post` calls `/sbin/ifup-local ${DEVICE}` so add there

.. code-block:: bash

   #!/bin/sh
   #/sbin/ifup-local ${DEVICE}

   if [[ "$1" == "br0" ]]
   then
     if [[ -e "/sys/devices/virtual/net/$1/bridge/multicast_snooping" ]]
     then
       echo "Setting /sys/devices/virtual/net/$1/bridge/multicast_snooping."
       echo 0 > /sys/devices/virtual/net/$1/bridge/multicast_snooping
     else
       echo "Warning: can not find /sys/devices/virtual/net/$1/bridge/multicast_snooping"
     fi
   #else
     #DO_NOTHING
   fi

iptables
--------

.. code-block:: none

   # multicast (igmp; Internet group management protocol)
   iptables -I INPUT -p igmp -j ACCEPT

   # Service config
   iptables -I INPUT -m addrtype --dst-type MULTICAST -m state --state NEW -m multiport -p udp -s 10.20.0.0/16 --dports 5404,5405 -j ACCEPT

   # iperf def port 
   iptables -I INPUT -m addrtype --dst-type MULTICAST -p udp --dport 5001 -j ACCEPT

test with iperf
---------------

Server:

.. code-block:: none

   # iperf -s -u -B 224.1.1.1 -i 1

Client:

.. code-block:: none

   # iperf -c 224.1.1.1 -u -T 32 -t 3

Problems:
- Things to watch out for. Apparently iperf has issues if the 'server' is running on a computer with multiple interfaces. But aside from that, this worked.
- Another thing to be careful of; the iperf test client will work correctly even if /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts is set (to 1). In this case, running iperf as a server and trying to ping the multicast address will NOT work. Whether this matters is dependent on your multicast needs.

netstat
-------

Show joined groups:

.. code-block:: none

   # netstat -g
   # cat /proc/net/igmp 
   # ip maddress list

tcpdump 
-------

Capture multicast traffic:

.. code-block:: none

   # tcpdump -n  -vv net 224.0.0.0/4

ping
----

.. code-block:: none

   # ping 224.1.1.1  Ping specific IP
   # ping 224.0.0.1  All hosts configured for multicast will respond with their IP addresses

