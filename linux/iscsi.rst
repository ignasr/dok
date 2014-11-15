iscsi
=====

discovery
---------

    ``iscsiadm -m discovery -t sendtargets -p 10.10.20.3`` show LUNs on target

creating targets
----------------

/etc/tgt/targets.conf

    ``service tgtd restart``

updating targets
----------------

    ``tgt-admin --update ALL --force`` to update your all your targets, incl. active ones (–-force)
    ``tgt-admin --update --tid=1 --force`` For updating Target ID 1

initiator side
``````````````

    ``iscsiadm -m session -r $SID --rescan``

you get the SID from iscsiadm -m session (it is the value in the []) or if you do iscsiadm -m session -P 3 you can see which session lines with with which lun. Or

    ``iscsiadm -m node -T target --rescan``

or you can just take the lazy way and do

    ``iscsiadm -m session --rescan``

    ``iscsiadm -m node -R`` only adds, does not delete

info
----

    ``tgt-admin --show``

    ``tgt-admin --dump`` dump konfig
