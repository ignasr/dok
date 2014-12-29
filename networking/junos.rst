junos
=====

.. code-block:: none

    ## root cli
    root% cli
    ## junos cli, op mode
    user@host>
    > show | compare
    > configure
    ## conf mode
    # run show configuration
    # exit

    show security policies from-zone z_1 to-zone z_2
    show configuration | display set
    commit

Common conf commands::

    set
    delete
    show
    commit
    copy
    rename

    set security zones security-zone z_1 address-book address a_1 10.0.0.2
    set security policies from-zone z_1 to-zone z_2 policy pol_1 match source-address [ n_1 n_2 ] destination-address as_1 application [ junos-http junos-https ]
    set security policies from-zone z_1 to-zone z_2 policy pol_1 then permit

links
-----

SRX getting started: http://kb.juniper.net/InfoCenter/index?page=content&id=KB15694

