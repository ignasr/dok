mysql
=====

information
-----------

.. code-block:: none

    # mysqladmin status
    # mysqladmin processlist
    > show status like '%onn%';
    > show processlist;

Table info::

    describe mysql.user;

Table sizes::

    # SELECT table_schema AS "Database name", SUM(data_length + index_length) / 1024 / 1024 AS "Size (MB)" FROM information_schema.TABLES GROUP BY table_schema;

User info::

    SELECT User, Host, Password FROM mysql.user;
    SELECT CONCAT(QUOTE(user),'@',QUOTE(host)) UserAccount FROM mysql.user;
    SHOW GRANTS;
    SHOW GRANTS FOR CURRENT_USER;
    SHOW GRANTS FOR 'root'@'localhost';

Replication::

    reset master;

Dumping and restoring
---------------------

grep a table from full dump::

    time sed -n -e '/DROP TABLE.*`mytable`/,/UNLOCK TABLES/p' mydump.sql > tabledump.sql
