elasticsearch
=============

status
------

.. code-block:: none

    curl -XGET 'http://localhost:9200/_cluster/health?pretty=true'
    curl -XGET 'http://localhost:9200/_status?pretty=1'
    curl -XGET localhost:9200/_stats?pretty=true
    curl http://localhost:9200/_aliases?pretty=1
