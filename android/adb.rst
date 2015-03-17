adb
===

connecting
----------

.. code-block: none

    sudo adb kill-server
    sudo adb start-server
    adb devices
    adb connect 127.0.0.1:5037

installing recovery
-------------------

Installing modified TWRP::

    adb sideload TWRP-2.8.5.0-F2FS.zip

getting logs
------------


.. code-block: none

    adb pull /tmp/recovery.log

