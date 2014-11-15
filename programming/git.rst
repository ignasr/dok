git
===

Rename a local branch
---------------------

``git branch -m <oldname> <newname>``

If you want to rename the current branch, you can simply do:

``git branch -m <newname>``

Commit squashing
----------------

http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html

Commits must not be pushed. This will do interactive squashing of 4 last commits:

``git rebase -i HEAD~4``


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

