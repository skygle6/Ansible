Certainly! Here are some examples to illustrate the concepts of advanced inventory management in Ansible:

**Group Variables:**
Assume you have a group named `webservers`, and you want to define common variables for all hosts within that group. Create a file named `webservers.yml` within the `group_vars` directory and define the variables:

```yaml
# group_vars/webservers.yml
---
web_server_port: 8080
web_server_user: myuser
```

Now, when executing tasks on hosts belonging to the `webservers` group, Ansible will automatically apply the `web_server_port` and `web_server_user` variables.

**Host Variables:**
Suppose you have a specific host named `web1.example.com` that requires specific configuration. Create a file named `web1.example.com.yml` within the `host_vars` directory and define the variables:

```yaml
# host_vars/web1.example.com.yml
---
web_server_port: 8888
web_server_user: admin
```

Ansible will load the `web1.example.com.yml` file when executing tasks on the `web1.example.com` host, overriding any variables defined in group variables or elsewhere.

**Nested Groups:**
Assume you have a group named `webservers` and want to further categorize hosts into frontend and backend servers. Create a directory named `webservers` within the `group_vars` directory, and inside it, create two files: `frontend.yml` and `backend.yml`. Define group-specific variables in each file:

```yaml
# group_vars/webservers/frontend.yml
---
web_server_port: 80
frontend_specific_variable: value1
```

```yaml
# group_vars/webservers/backend.yml
---
web_server_port: 8080
backend_specific_variable: value2
```

When executing tasks on hosts within the `webservers/frontend` or `webservers/backend` groups, Ansible will load the corresponding group variables in addition to the common variables defined in `webservers.yml`.

**Dynamic Inventory:**
You can use dynamic inventory scripts to generate inventory information dynamically. Ansible includes a few built-in dynamic inventory scripts, such as the `ec2.py` script for Amazon EC2. The dynamic inventory script retrieves information about EC2 instances and generates an inventory based on their attributes (e.g., tags, security groups).

To use the `ec2.py` dynamic inventory script, create a file named `ec2.ini` in the same directory as your playbook and specify the necessary configuration, such as access credentials. Then, you can use the generated inventory to execute tasks on your EC2 instances.

These examples demonstrate how advanced inventory management in Ansible allows you to define variables at different levels (groups, hosts), organize hosts into nested groups, and generate inventory dynamically from external sources. These features provide flexibility and customization options for managing your infrastructure using Ansible.