SELinux
=======

.. highlight:: none

.. code-block:: none

   semodule -DB  : enable full logging
   semanage fcontext -a -t virt_etc_t '/shared(/.*)?'
   restorecon -r /shared

starting auditd (selaert)
-------------------------

.. code-block:: none

    # yum install setroubleshoot-server
    # service messagebus start
    # service auditd restart

More: auditd http://blog.esmnetworks.com/ 

actions with files
------------------

Defaults::

    $ matchpathcon /var/spool/rsyslog

Set context to default::

    # restorecon -F /katalogas
    # restorecon -v /var/www/html/index.html

File se types::

    # file_context somewhere /etc/selinux

Change::

    # chcon -R --reference=/etc/kazkas /target/dir 
    # chcon -R -u system_u -t public_content_t /ftp
    # chcon -u system_u -r object_r -t tmp_t /tmppt


fcontext
````````

.. code-block:: none

    # matchpathcon /exports/foobar
    # semanage fcontext -a -t httpd_sys_content_t "/html(/.*)?"
        -a :: add
        -u :: user
        -r :: role
        -t :: type
    # semanage permissive -a httpd_t
    # restorecon -Rv /var/www/html
        -n :: noop

actions with users
------------------

.. code-block:: none

    unconfined_u
    guest_u
    xguest_u
    user_u
    staff_u

List selinux users::

    # semanage user -l

Change existing user se type::

    # semanage login -a [-s user_u] michael
        -a add
        -s user role

or::

    # usermod -Z user_u USERNAME

Change default se type (all default users will be changed also)::

    # semanage login -m -S targeted -s “user_u” -r s0 __default__

Hmm... something::

    # semanage user -m -R"unconfined_r webadm_r staff_r" staff_u

actions with ports
------------------

List::

    # semanage port -l| grep syslog

Add::

    # sudo semanage port -a -t syslogd_port_t -p tcp 7514

actions with processes
---------------------

Check if httpd is protected with SELinux::

    # ps -ZC httpd

List all::

    # ps -eZ

SE status::

    # sestatus

bools
-----

.. code-block:: none

    # sudo setsebool -P httpd_setrlimit 1
    # sudo setsebool -P allow_ypbind 1 - kad servisai laisvai galetu jungtis prie portu

    # getsebool -a
    # /usr/sbin/getsebool -a | grep samba

analyzing the logs
------------------

Aureport::

    # aureport -a
    # aureport --start today --event --summary -i

http://dgz.dyndns.org/mediawiki/index.php/(RHEL)_HOWTO_configure_the_auditing_of_the_system_(auditd)

Logs can be in  messages, user and /var/log/audit/audit.log

.. code-block:: none

    # sealert -l bf5c9ba8-3e2b-4780-b6aa-62861de64e7e

Generate sealert messeges from audit.log::

    # grep AVC /var/log/audit/audit.log | sedispatch

    # ausearch -m avc
    # ausearch -m avc -ts today
    # ausearch -m avc -if ./audit.log
    # ausearch -m avc -c sudo
        -c search in executables name

    # sealert -a /var/log/audit/audit.log

    # grep 945172 /var/log/audit/audit.log | audit2allow -w

seasearch
---------

.. code-block:: none

    # sesearch --allow -s cvs_t -c dir -p search

What can user_t do::

    # sesearch -A -s user_t
    # sesearch -A -s user_t | grep var_log
     
    # sesearch -A -s passenger_t -t passenger_t -c capability -p sys_resource
    # sesearch -t passenger_t
        -A :: search for allow rules



Log all (disable DontAudit)::

    (13:00:23) siXy: r2bit: dontaudit rules can be disabled for testing
    (13:00:55) siXy: semodule -DB (then -B to reenable them after)

working with modules
--------------------

List::
    # semodule -l

Compile::

    # audit2allow -a -m dansguardian > dansguardian.te
    # checkmodule -M -m dansguardian.te 
    # checkmodule -M -m dansguardian.te -o dansguardian.mod
    # semodule_package -o dansguardian.pp -m dansguardian.mod

Install::

    # semodule -i dansguardian.pp 

Files
-----

.. code-block:: none

    /etc/selinux
    /etc/selinux/targeted/contexts/files 
        ./file_contexts  - baseline file contexts for the entire system
        ./file_contexts.homedirs - for /home and subdirs
        ./media - for removable media

module config-history
---------------------

.. code-block:: none

    (3:58:05 PM) grift: yes some stupid bug
    (3:58:08 PM) grift: try this:
    (3:58:24 PM) grift: cat > mytest.te <<EOF
    (3:58:37 PM) grift: policy_module(mytest, 1.0)
    (3:58:41 PM) grift: EOF
    (3:58:47 PM) grift: cat > mytest.fc <<EOF
    (3:59:06 PM) grift:  /root/mydir/.* <<none>>
    (3:59:08 PM) grift: EOF
    (3:59:24 PM) grift: make -f /usr/share/selinux/devel/Makefile mytest.pp
    (3:59:30 PM) grift: semodule -i mytest.pp
    (3:59:37 PM) grift: matchpathon /root/mydir/test
    
    cat > mytest.te <<EOF
    policy_module(mytest, 1.0)
    EOF
    cat > mytest.fc <<EOF
    /root/mydir/.* <<none>>
    EOF
    
    make -f /usr/share/selinux/devel/Makefile mytest.pp
    semodule -i mytest.pp
    matchpathon /root/mydir/test

building a module 2
-------------------

http://www.gentoo.org/proj/en/hardened/selinux/selinux-handbook.xml?part=2&chap=5

.. code-block:: none

    Iskarpos:
    allow unconfined_t ext_gateway_t : process transition;
    allow unconfined_t secure_services_exec_t : file { execute read getattr };
    allow ext_gateway_t in_file_t : file { write create getattr };
    allow httpd_sys_script_t net_conf_t:file { open read getattr };
    allow ext_gateway_t in_queue_t : dir { write search add_name };
    
    module mysasl 1.0;
    require {
            type var_spool_t;
            type postfix_spool_t;
            type saslauthd_t;
            type saslauthd_var_run_t;
            class dir search;}
    #============= saslauthd_t ==============
    allow saslauthd_t var_spool_t:dir search;
    allow saslauthd_t postfix_spool_t:dir search;
    
    
    module myawstats 1.0;
    require {
            type httpd_awstats_script_t;
            type httpd_sys_script_exec_t;
            class dir { search getattr }; }
    #============= httpd_awstats_script_t ==============
    allow httpd_awstats_script_t httpd_sys_script_exec_t:dir search;
    
    require {
           type var_lib_t;
           class file { append getattr read open };}
    
macro list
----------

.. code-block:: none

    (23:15:15) sauleta: is there a way to list available macros? I tried semanage interface -l, but had no luck
    (23:20:47) grift: install selinux-policy-docs
    (23:22:00) grift: selinux-policy-doc
    (23:22:56) grift: then firefox /usr/share/doc/selinux-policy-3.10.0/html/index.html
    (23:23:10) grift: not all macros but quite a few
    (23:24:07) grift: you can also cat all the .if files in the various dirs in /usr/share/selinu/devel/include
    (23:24:34) grift: and the files in the support dir thats also in there

links
-----

SELinux intro: http://beginlinux.com/server_training/web-server/976-apache-and-selinux
and: http://wiki.centos.org/HowTos/SELinux 
reference policy: http://oss.tresys.com/projects/refpolicy 
Booleans: http://wiki.centos.org/TipsAndTricks/SelinuxBooleans
Issamus fedoros FAQ: http://docs.fedoraproject.org/en-US/Fedora/13/html/SELinux_FAQ/index.html#id4621954,
http://selinuxproject.org/
http://www.gentoo.org/proj/en/hardened/selinux/selinux-handbook.xml
https://www.wzdftpd.net/docs/selinux/references.html
Confining a process: http://www.adelton.com/docs/spacewalk/selinux-how-we-confined-spacewalk
