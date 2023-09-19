In Ansible, modules are reusable units of code that perform specific actions or tasks on target hosts. Modules are used within playbooks to define the tasks you want to execute. Ansible provides a wide range of built-in modules that cover various areas such as system administration, network configuration, cloud management, file manipulation, and more.

Here are a few commonly used modules in Ansible playbooks:

**1. Command Execution Modules:**
- `command` or `shell`: Executes commands on the target host's command line.
- `script`: Runs a local script on the target host.
- `raw`: Executes a command without going through the module subsystem.

**2. Package Modules:**
- `apt` (for Debian/Ubuntu) or `yum` (for Red Hat/CentOS): Installs, upgrades, or removes packages.
- `dnf` (for Fedora): Manages packages using the DNF package manager.
- `pip` or `pip3`: Installs Python packages.

**3. File Modules:**
- `copy`: Copies files from the control machine to the target hosts.
- `template`: Renders templates on the control machine and copies them to the target hosts.
- `lineinfile`: Manages lines in a file.
- `file`: Manages file attributes like permissions, ownership, and symlinks.

**4. Service Modules:**
- `service`: Manages services on the target hosts (e.g., starting, stopping, restarting).

**5. System Modules:**
- `user`: Manages user accounts on the target hosts.
- `group`: Manages user groups on the target hosts.
- `cron`: Manages cron jobs.

**6. Cloud Modules:**
- `ec2`: Manages Amazon EC2 instances.
- `azure_rm_virtualmachine` or `azure_rm` (for Azure): Manages Azure virtual machines and resources.
- `gcp_compute_instance` or `gcp` (for Google Cloud): Manages Google Cloud Platform instances and resources.

These are just a few examples, and Ansible provides numerous other modules to automate various tasks. You can explore the Ansible documentation (https://docs.ansible.com/ansible/latest/modules/modules_by_category.html) to see the full list of available modules and their usage details.

To use a module in your playbook, you include it as a task in a play, providing the necessary parameters specific to that module. Each module has its own set of parameters and options, which you can configure based on your requirements.

Using modules in playbooks allows you to abstract away the low-level details and focus on describing the desired state of your systems and infrastructure, making your automation tasks more concise, reusable, and manageable.