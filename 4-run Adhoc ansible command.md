Some examples of common Ansible commands and their usage. You can run these commands on your own Ansible control node or workstation.

1. **Ping all hosts in inventory:**

   ```
   ansible all -m ping
   ```

   This command pings all the hosts defined in your inventory file.

2. **Run a command on remote hosts:**

   ```
   ansible all -a "command"
   ```

   Replace `"command"` with the actual command you want to run on the remote hosts. For example:

   ```
   ansible all -a "uname -a"
   ```

   This command runs the `uname -a` command on all the hosts in your inventory.

3. **Execute a playbook:**

   ```
   ansible-playbook playbook.yml
   ```

   Replace `playbook.yml` with the filename of your playbook. This command runs the specified playbook, which contains a series of tasks defined in YAML format.

4. **Limit the playbook execution to specific hosts or groups:**

   ```
   ansible-playbook playbook.yml --limit "group1"
   ```

   Replace `"group1"` with the specific group or host you want to limit the playbook execution to. This command runs the playbook only on the hosts or group specified.

5. **Check the syntax of a playbook without executing it:**

   ```
   ansible-playbook playbook.yml --syntax-check
   ```

   This command checks the syntax of the playbook without executing it, helping you catch any syntax errors or formatting issues.

These are just a few examples of common Ansible commands. Ansible offers a wide range of modules and options to perform various tasks, from system administration to configuration management. You can refer to the Ansible documentation (https://docs.ansible.com) for more information on modules, playbooks, and advanced usage.