---
title: Ansible Ad Hoc Commands and Custom SSH Ports
date: 2023-08-15 13:54
---

# Ansible Ad Hoc Commands and Custom SSH Ports

When working with Ansible, ad hoc commands can be useful for quick tasks on remote servers. If you've customized the SSH port on your servers, it's crucial to configure Ansible correctly.

## Using an INI-style Inventory

Create an inventory file with IP addresses and custom SSH ports using the INI-style format:

```ini
[my_servers]
server1 ansible_host=[ipaddress] ansible_ssh_port=[port]
server2 ansible_host=[ipaddress] ansible_ssh_port=[port]


```


Replace [ipaddress] with the server's IP address and [port] with the configured SSH port.

## Using YAML Inventory

Alternatively, write the inventory in YAML format, which is more readable for complex setups:

```yaml

all:
  hosts:
    server1:
      ansible_host: [ipaddress]
      ansible_ssh_port: [port]
    server2:
      ansible_host: [ipaddress] 
      ansible_ssh_port: [port]
    server3:
      ansible_host: [ipaddress] 
      ansible_ssh_port: [port]


```

Replace [ipaddress] and [port] with the appropriate values.

To execute ad hoc commands using this inventory:

`ansible all -i inventory.ini -u [username] --private-key=[path/to/private/key/file] -m [module_name]
` 
