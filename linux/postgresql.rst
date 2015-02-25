postgresql
==========

info
----

.. code-block:: none

    psql postgres
    psql db_name

    \l  :: list databases
    \l+
    \d  :: show all tables, views, and sequences
    \d+

    \c db_name  :: change db

    \q  : quit

users
-----

.. code-block:: none

    ALTER USER postgres WITH PASSWORD 'tmppassword';  :: change root pw
    ALTER USER username WITH PASSWORD 'tmppassword';  :: change user pw

