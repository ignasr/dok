java
====

debug
-----

the hard way with visualvm
``````````````````````````

Debugging a remote java process.

Req localhost: visualvm
Req remote: java-devel

Target host.

Create file jstatd.all.policy::

    grant codebase "file:${java.home}/../lib/tools.jar" {
       permission java.security.AllPermission;
    };

Run::

    jstatd -p 8888 -J-Djava.security.policy=jstatd.all.policy

Local host.

Localhost tunnels through jump_server to target_host.

.. code-block:: none

    ssh -NL 9998:target_server:22 jump_server &
    ssh -ND 9696 -p 9998 localhost &
    jvisualvm -J-Dnetbeans.system_socks_proxy=localhost:9696 -J-Djava.net.useSystemProxies=true

In visualvm add statsd connection with port 8888.

No cpu stats etc. Use JMX connection for that.
