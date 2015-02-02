storcli
=======

Full info::

    storcli /c0 show

Physical drives::

    storcli /c0/eall/sall show
    storcli /c0/e64/s4,5,6,7 show

Drive groups::

    storcli /c0/dall show all

Virtual drives::

    storcli /c0/vall show

Creating RAID10
---------------

List new drives::

    storcli /c0/e64/s4,5,6,7 show

Change status of all drives to good, use force if status is JBOD::

    storcli /c0/e64/s4 set good

Show drive groups::

    storcli /c0/dall show all

If drive group is marked as foreign, and it shouldn't be, init it::

    storcli /c0/e64/s5 start initialization
    storcli /c0/e64/s5 show initialization

Create raid10 vd::

    storcli /c0 add vd r10 drives=64:4,64:5,64:6,64:7 pdperarray=2

If the new vd is not consistent, init it::

    storcli /c0/v1 show
    storcli /c0/v1 start init [full]
    storcli /c0/v1 show init 
