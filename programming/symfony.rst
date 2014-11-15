symfony
=======

default bundle tree
-------------------

.. code-block:: none

    $ tree src/Acme/StoreBundle/
    src/Acme/StoreBundle/
    |-- AcmeStoreBundle.php
    |-- Controller
    |   `-- DefaultController.php
    |-- DependencyInjection
    |   |-- AcmeStoreExtension.php
    |   `-- Configuration.php
    |-- Resources
    |   |-- config
    |   |   |-- routing.yml
    |   |   `-- services.yml
    |   |-- doc
    |   |   `-- index.rst
    |   |-- public
    |   |   |-- css
    |   |   |-- images
    |   |   `-- js
    |   |-- translations
    |   |   `-- messages.fr.xlf
    |   `-- views
    |       `-- Default
    |           `-- index.html.twig
    `-- Tests
        `-- Controller
            `-- DefaultControllerTest.php


console
-------

Create an AcmeStoreBundle:

.. code-block:: none

    php app/console generate:bundle --namespace=Acme/StoreBundle

Create a doctine db:

.. code-block:: none

    php app/console doctrine:database:create

Create an entity with doctrine:

.. code-block:: none

    php app/console doctrine:generate:entity
