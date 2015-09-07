vmware
======

tools
-----

centos 6
````````

Note: ESXi will show a grey sign "Tools installed (managed by guest)".

Install correct vmware-tools-repo version from https://packages.vmware.com/tools/index.html esx.

.. code-block:: none

   rpm --import https://packages.vmware.com/tools/keys/VMWARE-PACKAGING-GPG-RSA-KEY.pub
   yum install vmware-tools-esx-kmods vmware-tools-esx-nox

