git
===

rename a local branch
---------------------

``git branch -m <oldname> <newname>``

If you want to rename the current branch, you can simply do:

``git branch -m <newname>``

commit squashing
----------------

http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html

Commits must not be pushed. This will do interactive squashing of 4 last commits:

``git rebase -i HEAD~4``

log
---

.. code-block:: none

    git log --author=bob
    git log --pretty=oneline
    git log --graph --oneline --decorate --all
    git log --name-status

Show not pushed commits:::

    git log --branches --not --remotes
 
show
----

.. code-block:: none

    git show <treeish>:<file>
    git show HEAD~4:index.html
