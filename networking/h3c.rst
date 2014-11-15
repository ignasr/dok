h3c
===

information
-----------

interfaces
``````````

.. code-block:: none

   display interface brief
   display interface GigabitEthernet 1/0/11
   display interface Vlan-interface brief
   display interface Vlan-interface 100
   display vlan 100


configuration
-------------

configuration management
````````````````````````

.. code-block:: none

   display current-configuration
   display saved-configuration
   display this
   display startup
   reset saved-configuration
   save
   startup saved-configuration

create a trunk
``````````````

.. code-block:: none

   interface GigabitEthernet 1/0/10
   port link-type trunk
   port trunk permit vlan 807 808
    

change password
```````````````

.. code-block:: none

   password [ simple | cipher ] password
   undo password

   <H3C> system-view
   System View: return to User View with Ctrl+Z.
   [H3C] local-user test
   [H3C-luser-test] password
   Password:**********
   confirm:**********
   Updating the password file, please wait...


