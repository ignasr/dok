rpm
===

tools
-----

.. code-block:: none

    yum install rpmdevtools rpmlint
    rpmdev-setuptree
    # Install dependencies of the spec file
    yum-builddep -y collectd-5.4.1/contrib/redhat/collectd.spec

