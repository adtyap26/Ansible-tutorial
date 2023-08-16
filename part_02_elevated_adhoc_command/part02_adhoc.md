---
title: Running Elevated Ad-Hoc Commands with Ansible
date: 2023-08-16 14:35
---

# Running Elevated Ad-Hoc Commands with Ansible

When working with multiple servers that require different levels of permissions for certain tasks, Ansible's ad hoc commands can be a powerful tool to quickly execute commands across your infrastructure. This can be especially useful when performing tasks like updates and upgrades, where elevated privileges are required.

In this example, let's assume you have two servers: `server1` and `server2`, each with its own SSH password for authentication.

To run commands that require elevated privileges, such as system updates, you can use Ansible's `-b` or `--become` flag along with the appropriate options.

## Running Commands with Different Passwords

When the servers have different passwords, you can use separate commands for each server:

```sh
ansible server1 -u your_username -m apt -b -a "update_cache=yes upgrade=dist"
ansible server2 -u your_username -m apt -b -a "update_cache=yes upgrade=dist"
```

Replace your_username with your actual SSH username. These commands will prompt you for the SSH password of each server individually.

## Running Commands with the Same Password

If both servers share the same password, you can simplify the process using a single command:

`ansible all -u your_username -m apt --become --ask-become-pass`

Here, the --become flag enables privilege escalation, and the --ask-become-pass flag prompts you for the password once. This is particularly useful for running commands on multiple servers with the same elevated permissions.

Remember to adjust the commands according to your environment and requirements. Ansible's ad hoc commands provide a flexible way to manage tasks efficiently across your infrastructure.










