elasticsearch
=============

status
------

.. code-block:: none

    curl -XGET 'http://127.0.0.1:9200/_cluster/health?pretty'
    curl -XGET 'http://127.0.0.1:9200/_status?pretty'
    curl -XGET 'http://127.0.0.1:9200/_cat/shards'
    curl -XGET 'http://127.0.0.1:9200/_stats?pretty'
    curl -XGET 'http://127.0.0.1:9200/_aliases?pretty'
