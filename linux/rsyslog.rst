rsyslog
=======

debug
-----

Send a message with netcat::

    echo '<166>Jan 13 13:26:07 srv1.test nginx: resize1.ef.lan 172.18.70.38 - - ' | nc -v -u -w 0 127.0.0.1 514
