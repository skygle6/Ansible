To create an inventory file in Ansible, you need to follow these steps:

1. Open a text editor of your choice.
2. Start a new file and save it with a `.ini` extension (e.g., `inventory.ini`).
3. In the inventory file, you define groups of hosts and assign them to specific categories or variables.

Here's an example of an inventory file:

```plaintext
[web]
webserver1.example.com
webserver2.example.com
webserver3.example.com

[database]
dbserver1.example.com
dbserver2.example.com

[loadbalancer]
lb1.example.com
lb2.example.com
```

In this example, we have defined three groups: `[web]`, `[database]`, and `[loadbalancer]`. The hostnames listed under each group are the target hosts on which you want to execute Ansible tasks.

You can also assign variables to hosts or groups by using the following syntax:

```plaintext
[web]
webserver1.example.com ansible_user=ubuntu ansible_ssh_private_key_file=/path/to/private_key.pem

[database]
dbserver1.example.com ansible_user=admin ansible_password=secretpassword
```

In this case, we have assigned the `ansible_user` and `ansible_ssh_private_key_file` variables to the host `webserver1.example.com` under the `[web]` group. Similarly, the `ansible_user` and `ansible_password` variables are assigned to the host `dbserver1.example.com` under the `[database]` group.

You can customize your inventory file to match your specific environment and requirements. It's also possible to use dynamic inventory sources like cloud providers, external scripts, or configuration management systems.

Once you have created the inventory file, you can reference it in your Ansible commands or configuration files using the `-i` or `--inventory` option, followed by the path to your inventory file.

For example:
```shell
ansible-playbook -i inventory.ini playbook.yml
```

This tells Ansible to use the inventory file `inventory.ini` when executing the playbook `playbook.yml`.

Note: Besides the INI format, Ansible also supports other inventory formats like YAML and dynamic inventory scripts. The INI format is the most basic and widely used.

If you don't provide a username for a host in Ansible's inventory file, Ansible will use the default SSH user of your system. This default user can vary depending on the operating system you are running Ansible from.