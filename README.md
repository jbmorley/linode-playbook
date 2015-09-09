Linode Ansible Playbook
=======================

Ansible playbook for configuring and securing an Ubuntu 14.04.3 LTS Linode server and installing and configuing a basic Apache 2 instance.

Includes steps from the following guides:

- [Securing Your Server](https://www.linode.com/docs/security/securing-your-server/)


Running
-------

Update the hosts (`hosts`) file with details of your Linode server(s):

```
[linode]

192.168.144.173
192.168.144.174
```

Run the Ansible playbook and provide the relevant details when prompted:

```bash
ansible-playbook linode.yml --user root --ask-pass --ask-become-pass
```

N.B. The playbook cannot be run more than once with `--user root` as it disables remote access for the root user during configuration. If you wish to re-run the playbook to double-check it is complete, run it using the newly created user:

```bash
ansible-playbook linode.yml --user <new user> --ask-pass --ask-become-pass
```

Notes
-----

- The current user's SSH key (`./ssh/id_rsa.pub`) is used for configuring remote SSH access.
- Obviously it's possible to remove the interactive questions and tailor this to infrastructures with known users and passwords, but this is intended to provide a general solution.