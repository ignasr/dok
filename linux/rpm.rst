rpm
===

tools
-----

.. code-block:: none

    yum install rpmdevtools rpmlint
    rpmdev-setuptree
    # Install dependencies of the spec file
    yum-builddep -y collectd-5.4.1/contrib/redhat/collectd.spec

    rpm --eval "%{_datarootdir}"
    rpm --showrc | grep topdir

Installing dependencies:

.. code-block:: none

    yum-builddep [package]

srpm
----

.. code-block:: none

    rpm -qpi some.src.rpm
    rpm2cpio some.src.rpm | cpio -idmv
