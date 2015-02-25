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
    \dt  :: tables
    \dv  :: views

    \c db_name  :: change db

    \timing  :: timing on/off

    select version();

    \e  :: use an editor to type the command
    \q  :: quit

help
----

.. code-block:: none

    \?
    \h CREATE
    \h CREATE INDEX

users
-----

.. code-block:: none

    ALTER USER postgres WITH PASSWORD 'tmppassword';  :: change root pw
    ALTER USER username WITH PASSWORD 'tmppassword';  :: change user pw

databases
---------

.. code-block:: none

    CREATE DATABASE mydb WITH OWNER ramesh;
    DROP DATABASE mydb;
