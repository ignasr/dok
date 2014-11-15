clustering
==========

Cluster is split into two components; cluster communication managed by cman and resource management provided by rgmanager.

tools
-----

.. code-block:: none

   cman_tool nodes
   ccs_config_validate
   cman_tool version
   cman_tool version -r
   clustat

List DLM lockspaces:

.. code-block:: none

   dlm_tool ls

Fence status tikrinimas, kai cman veikia:

.. code-block:: none

   fence_check

managing a cluster
------------------

.. code-block:: none

   clusvcadm -e <service> -m <node>
   clusvcadm -d <service>
   clusvcadm -e vm:vm01-win2008 -m an-c05n01.alteeve.ca  :: start (enable) a vm
   clusvcadm -d vm:vm01-win2008  :: shutdown (disable) a vm
   clusvcadm -M vm:vm01-win2008 -m an-c05n02.alteeve.ca  :: live migrate a vm

Rebooting a cluster node
------------------------

- Stop rgmanager, cman on every node that is to be restarted (mind the quorum).

- Reboot.

- Start cman, rgmanager.

clvm
----

Start only when cman is running and cluster is healthy.

links
-----

https://alteeve.ca/w/AN!Cluster_Tutorial_2
