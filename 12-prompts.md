In Ansible, you can use the `vars_prompt` or `vars_files` directives to prompt the user for input during playbook execution. These directives allow you to gather information interactively from the user running the playbook.

1. **vars_prompt:**
The `vars_prompt` directive allows you to define variables and prompt the user for their values. It displays a prompt to the user and waits for their input. Here's an example:

```yaml
---
- name: Example Playbook with vars_prompt
  hosts: all
  vars_prompt:
    - name: username
      prompt: "Enter your username: "
    - name: password
      prompt: "Enter your password: "
      private: yes

  tasks:
    - name: Print entered values
      debug:
        var: username
    - name: Another task
      debug:
        var: password
```

In this example, the `vars_prompt` directive is used to prompt the user for their `username` and `password`. The `prompt` attribute specifies the message to display as the prompt. The `private` attribute is set to `yes` for the `password` variable to hide the user's input during entry. The entered values are then printed using the `debug` module.

2. **vars_files:**
The `vars_files` directive allows you to load variable values from external files. You can create a file containing the variables and their values, and Ansible will load them during playbook execution. Here's an example:

```yaml
---
- name: Example Playbook with vars_files
  hosts: all
  vars_files:
    - vars.yml

  tasks:
    - name: Print variable value
      debug:
        var: my_variable
```

In this example, the `vars_files` directive is used to load variables from the `vars.yml` file. The `vars.yml` file should contain variable definitions in YAML format, like this:

```yaml
# vars.yml
---
my_variable: Hello, Ansible!
```

The `my_variable` value from the `vars.yml` file is then printed using the `debug` module.

These are two ways to incorporate prompts in your Ansible playbooks. You can choose the appropriate method based on your requirements and the desired level of user interaction.