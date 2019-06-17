# proactcloud.admins

This role will configure a Linux system with neccessary user infrastructure for the admins, an ssh_allow group, SSH Key deployment and the appropriate user accounts. Specifically this role will create all users from the admins_users dictionary with the appropriate settings and SSH Keys (exclusively!). Root will only have a singular SSH key (this is enforced!), which is taken from pacadmins_root_ssh_key

Admin UIDs are expected to be in the 10000 - 20000 range (inclusive). In the future this script may also allow normal users to be created (no admins, no sudo etc.), which will then be in the 1000-9999 UID range.

UIDs above 20000 will then be considered "rogue" (except for nobody etc.) and will be purged.

## Requirements

None.

## Role Variables

* pacadmins_admin_users: dictionary for each user to be created and enabled:
  * Example:
    pacadmins_admin_users:
      username1:
        fullname: Hans W. User
        uid: 10000
        sshkey: "ssh-ed25519 AAAAC3NzaC1lDHZ%NTE5AAAAIIPc1iBgkjhf/KJNWD726KGAOnZtJbvFL35l3ZByz Hans W. User, <hansw@example.com>, 2017-02-05"
* pacadmins_purge_admin: dictionary of admins to remove from systems. Identical to pacadmins_admin_users dictionary.
* pacadmins_root_ssh_key: SSH (public) key for direct access to root. Will be deployed into root account.

## Dependencies

None.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      include_vars: my_admins.yml
      roles:
         - { role: proactcloud.admins }

## License

Copyright 2019 Proact Deutschland GmbH

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

<http://www.apache.org/licenses/LICENSE-2.0>

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## Author Information

Patrick Dreker (patrick.dreker@proact.de)
