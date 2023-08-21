---
title: Creating the first playbook
date: 2023-08-21 14:21 
---

# Ansible Playbook Tutorial

In this tutorial, we'll walk through the process of creating an Ansible playbook to automate tasks on remote servers. We'll start with a basic example and gradually build upon it.

## Step 1: Create a Playbook File

Create a new `.yml` file for your playbook. Let's name it `my_playbook.yml`.

## Step 2: Define a Play

In your playbook file, define a play. A play consists of tasks that target specific hosts. Here's a simple example:

   ```yaml
   ---
   - name: My First Play
     hosts: server1
     become: true
     tasks:
       - name: Ensure Nginx is installed
         apt:
           name: nginx
           state: present
   ```

Replace server1 with the name of your host as defined in your inventory.

## Step 3: Define Tasks
Under the tasks section of your play, define tasks that you want to execute on the target host. Tasks use modules to perform actions. In this example, we're using the apt module to install Nginx.
Step 4: Run the Playbook
Open a terminal and navigate to the directory containing your playbook.

Run the playbook using the ansible-playbook command:

`ansible-playbook my_playbook.yml -i inventory.ini`

Replace inventory.ini with the path to your inventory file.


### Managing Servers with Custom SSH Ports

If your servers have custom SSH ports, you can adjust your playbook accordingly:

Update your inventory file to include the custom SSH ports for each server:

`server1 ansible_host=<ipaddress> ansible_ssh_port=<port>`

```yaml

- name: My First Play
  hosts: server1
  become: true
  tasks:
    - name: Ensure Nginx is installed
      apt:
        name: nginx
        state: present
      when: ansible_port == <custom_ssh_port>


```

Replace <custom_ssh_port> with the actual custom SSH port you've configured for the server.

With these adjustments, your playbook will execute tasks based on the correct custom SSH port for each server.

Remember to adjust the playbook, inventory, and custom SSH port values according to your environment.

Happy automating!

