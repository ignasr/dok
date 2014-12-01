junos
=====

.. code-block:: none

    > configure
    # show | compare
    # show security policies from-zone z_1 to-zone z_2

    # set security zones security-zone z_1 address-book address a_1 10.0.0.2
    # set security policies from-zone z_1 to-zone z_2 policy pol_1 match source-address [ n_1 n_2 ] destination-address as_1 application [ junos-http junos-https ]
    # set security policies from-zone z_1 to-zone z_2 policy pol_1 then permit

