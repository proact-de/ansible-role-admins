teamix.admins
=============

This role will configure a Linux system with neccessary user infrastructure for the admins, which includes sudo without PW, an ssh_allow group, SSH Key deployment and the appropriate user accounts. Specifically this role will create all users from the admins_users dictionary with the appropriate settings and SSH Keys (exclusively!). All SSH Keys from admin_users will also be added to the root account, as well as the SSH Key from "ansible_ssh_key".

Requirements
------------

None.

Role Variables
--------------

* tmxadmins_admin_users: dictionary for each user to be created and enabled:
  * Example:
    tmxadmins_admin_users:
      username1:
        fullname: Hans W. User
        uid: 10000
        sshkey: "ssh-ed25519 AAAAC3NzaC1lDHZ%NTE5AAAAIIPc1iBgkjhf/KJNWD726KGAOnZtJbvFL35l3ZByz Hans W. User, <hansw@example.com>, 2017-02-05"
* tmxadmins_purge_admin: dictionary of admins to remove from systems. Identical to tmxadmins_admin_users dictionary.
* tmxadmins_ansible_ssh_key: SSH (public) key for access using ansible. Will be deployed into root account.

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      include_vars: my_admins.yml
      roles:
         - { role: teamix.admins }

License
-------

BSD

Author Information
------------------
Patrick Dreker (patrick.dreker@teamix.de)
Source Code: https://bitbucket.devops.lab.teamix.net:8443/projects/CD/repos/teamix.admins/
