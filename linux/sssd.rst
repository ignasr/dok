sssd
====

host authorisation
------------------

https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/config-sssd-domain-access.html

3 Possiblilities:
- Simple Access Provider
- LDAP Access Filter
- authorizedService or host attribute in an entry

access filter and groups
````````````````````````

http://thornelabs.net/2013/01/28/linux-restrict-server-login-via-ldap-groups.html

.. code-block:: none

   access_provider = ldap
   ldap_access_filter = memberOf=cn=Group Name,ou=Groups,dc=thornelabs,dc=net


