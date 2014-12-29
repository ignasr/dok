salt
====

cmd
---

.. code-block:: none

    salt-key -L
    salt-key -a s.vagrant.localdomain
    salt-key -A
    
    salt '<target>' <function> [arguments]
    salt '*' test.ping
    salt '*' cmd.run 'uname -a'
    salt -G 'os:Ubuntu' test.ping
    salt -E 'virtmach[0-9]' test.ping
    salt -L 'foo,bar,baz,quo' test.ping
    salt -C 'G@os:Ubuntu and webser* or E@database.*' test.ping
    # List all available functions
    salt '*' sys.doc
    salt '*' cmd.exec_code python 'import sys; print sys.version'
    salt '*' pip.install salt timeout=5 upgrade=True

    salt-call -l debug state.highstate
    salt '*' test.ping --out txt
    salt '*' test.ping --out yaml
    salt '*' test.ping --out raw
    salt '*' test.ping --static --out json

    salt '*' test.version
    salt-run manage.versions
    salt '*' pkg.install salt-minion refresh=True

    salt '*' pkg.install nginx
    salt '*' service.start nginx
    salt '*' disk.usage
    salt '*' network.interfaces
    salt '*' sys.doc | less
    salt '*' grains.items

installing
----------

.. code-block:: none

    yum install http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
    cd /etc/yum.repos.d/
    #overrides 2 epel pkgs.
    wget http://copr.fedoraproject.org/coprs/saltstack/zeromq4/repo/epel-6/saltstack-zeromq4-epel-6.repo


installing minion
`````````````````

.. code-block:: none

    yum install salt-minion
    sed -ie 's/#master: salt/master: s/' /etc/salt/minion
    chkconfig salt-minion on
    service salt-minion start

installing master
`````````````````

.. code-block:: none

    yum install salt-master
    lokkit -p 4505:tcp -p 4506:tcp
    chkconfig salt-master on
    service salt-master start

links
-----

https://github.com/saltstack-formulas
http://www.willdurness.com/post/101277984950/salt-pillar-driven-design-pattern

