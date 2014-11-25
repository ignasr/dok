gitlab
======

Create Repository (gitlab)
--------------------------

.. code-block:: none

    mkdir aliases
    cd aliases
    git init
    touch README
    git add README
    git commit -m 'first commit'
    git remote add origin gitlab@fqdn:puppet2/aliases.git
    git push -u origin master


Existing Git Repo? (gitlab)
---------------------------

.. code-block:: none

    cd existing_git_repo
    git remote add origin gitlab@fqdn:puppet2/aliases.git
    git push -u origin master

