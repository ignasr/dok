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

