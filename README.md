teamix.admins
=============

This role will configure a Linux system with neccessary user infrastructure for the admins, which includes sudo without PW, an ssh_allow group, SSH Key deployment and the appropriate user accounts. Specifically this role will create all users from the admins_users dictionary with the appropriate settings and SSH Keys (exclusively!). All SSH Keys from admin_users will also be added to the root account, as well as the SSH Key from "ansible_ssh_key".

Requirements
------------

None.

Role Variables
--------------

* admin_users: dictionary for each user to be created and enabled:
  * Example:
    admin_users:
      username1:
        fullname: Hans W. User
        uid: 10000
        sshkey: "ssh-ed25519 AAAAC3NzaC1lDHZ%NTE5AAAAIIPc1iBgkjhf/KJNWD726KGAOnZtJbvFL35l3ZByz Hans W. User, <hansw@example.com>, 2017-02-05"
* purge_admin: dictionary of admins to remove from systems. Identical to admin_users array.
* ansible_ssh_key: SSH (public) key for access using ansible. will be deployed into root account.

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

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
