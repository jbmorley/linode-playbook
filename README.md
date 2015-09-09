Linode Ansible Playbook
=======================

Ansible playbook for configuring and securing an Ubuntu 14.04.3 LTS Linode server.

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
ansible-playbook linode.yml --ask-pass --ask-become-pass
```

Notes
-----

- The current user's SSH key (`./ssh/id_rsa.pub`) is used for configuring remote SSH access.
- The playbook cannot be run more than once as it relies on SSH access for the remote root user which is disabled during configuration.
- Obviously it's possible to remove the interactive questions and tailor this to infrastructures with known users and passwords, but this is intended to provide a general solution.