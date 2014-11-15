SmartOS
=======

Files: https://download.joyent.com/pub/iso/

KVM -> SmartOS http://www.the-mesh.org/content/building-smartos-home-data-center
Blog: http://blog.smartcore.net.au/posts/
VRRP: http://www.c0t0d0s0.org/archives/7549-Less-known-Solaris-Features-Highly-available-loadbalancing..html

vmware
------

Disk controller: LSI Logic Parallel

Info
----

Cheat sheept: http://wiki.joyent.com/wiki/display/jpc2/The+Joyent+Linux-to-SmartOS+Cheat+Sheet

prstat -Z

Configuring
-----------

Changing the hostname
`````````````````````

http://wiki.smartos.org/display/DOC/Administering+the+Global+Zone

Changin def vnc port
````````````````````

vmadm update dece98e8-29d7-4394-8cf1-d0185e2258b7 vnc_port=35351
