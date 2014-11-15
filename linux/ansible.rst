ansible
=======

Configuring hosts
-----------------

File `/etc/ansible/hosts`

    ansible vu-prod -m ping
    ansible "~(host1|host2)" -m ping

ssh-agent
---------

    ssh-agent bash
    ssh-add -t 8h ~/.ssh/id_my

List all current keys:

    ssh-add -l

Delete all current keys:

    ssh-add -D

Commands
--------

Safe, one cmd, uses `command` module:

    ansible all -a "/bin/echo hello"

Multiple cmds, uses `shell` module. Attention to quoting:

    ansible all -m shell -a '/usr/sbin/sestatus | grep status'

Sudo command:

    ansible vu -a 'find /etc/sudoers.d -type f' --sudo
