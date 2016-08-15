# selinux module
===

[![Build Status](https://api.travis-ci.org/ghoneycutt/puppet-module-selinux.png)](https://travis-ci.org/ghoneycutt/puppet-module-selinux)

This module manages the SELinux configuration file.

===

# Compability

This module has been tested to work on the following systems with Puppet v3 and Ruby versions 1.8.7, 1.9.3 and 2.0.0.

 * EL 5
 * EL 6

===

# Parameters

See man page selinux(8) for more information regarding the configuration settings.


mode
----
Operation mode of SELinux, valid values are 'enforcing', 'permissive' and 'disabled'.

- *Default*: 'disabled'

type
----
The type of policies in use, valid values are 'targeted' and 'strict'.

- *Default*: 'targeted'

setlocaldefs
------------
String to pass to SETLOCALDEFS option. Valid values are '0' and '1'.

- *Default*: undef

config_file
-----------
The path to the selinux configuration path to manage.

- *Default*: '/etc/selinux/config'

policytools
-----------
If true, manage the `policycoreutils-python` package.  The purpose of this
behavior is to provide the `semanage` command, e.g. to reconfigure the selinux
policy such that `restorecon` will restore a file to the desired state.  For
example, to enable SSH key based login for an user account outside of the normal
location:

    semanage fcontext -a -t ssh_home_t /var/lib/git/.ssh
    semanage fcontext -a -t ssh_home_t /var/lib/git/.ssh/authorized_keys
    restorecon -v /var/lib/git/.ssh/
    restorecon -v /var/lib/git/.ssh/authorized_keys

- *Default*: false
