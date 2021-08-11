A Simple Shell Script to Authenticate Against LDAP
==================================================

This is a simple but extensible shell script to authenticate users by
binding to LDAP. Additional checks, such as requiring group memberships,
can easily be configured. The credentials are read from environment
variables. In case of a successful authentication, it exits with exit
code 0, non-zero otherwise.

ldap-auth-sh is known to work with:

* **OpenVPN** (via the ``--auth-user-pass-verify`` option)
* **Home Assistant** (via the upcoming ``command_line`` auth provider)

However, it's of course not limited to these platforms.

This fork adds an additional authentication type, `ldapsearch_searchdn`,
which supports using an external search DN (e.g. an administrator account)
to find a user based on the `FILTER` and get its DN and other `ATTRS`,
then uses `ldapwhoami` to perform the actual authentication. This allows
one to use any LDAP field to find the user they wish. An example config is
provided in the `examples/` folder.


Requirements
------------

You need:

* a POSIX-compliant shell with ``cat``, ``grep`` and ``sed`` (even
  BusyBox will do)
* a compatible LDAP client, currently one of

  * ``curl`` (with ``ldap`` protocol support compiled in, verify with
    ``curl --version``)
  * ``ldapsearch``


Getting Started
---------------

Just copy the file `ldap-auth.sh <ldap-auth.sh>`_ and read the comments
therein.

Sample configurations are shipped in the `examples <examples>`_ directory.
