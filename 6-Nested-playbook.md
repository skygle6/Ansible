In Ansible, you can call one playbook from another playbook using the `include` or `import_playbook` directive. This allows you to reuse and organize your automation logic across multiple playbooks.

Here's an example of how to call one playbook from another:

**Parent Playbook (`parent.yml`):**
```yaml
---
- name: Parent Playbook
  hosts: target_hosts
  tasks:
    - name: Include Child Playbook
      include: child.yml
```

**Child Playbook (`child.yml`):**
```yaml
---
- name: Child Playbook
  tasks:
    - name: Task 1
      # Task 1 details

    - name: Task 2
      # Task 2 details
```

In this example, the parent playbook (`parent.yml`) includes the child playbook (`child.yml`) using the `include` directive. When the parent playbook is executed, it will include the tasks defined in the child playbook as part of its execution.

You can run the parent playbook with the `ansible-playbook` command:
```plaintext
ansible-playbook parent.yml
```

During execution, Ansible will first process the tasks in the parent playbook and then include and execute the tasks from the child playbook.

Alternatively, you can use the `import_playbook` directive instead of `include` if you prefer the child playbook to be run separately as a separate play. Here's an example:

**Parent Playbook (`parent.yml`):**
```yaml
---
- name: Parent Playbook
  hosts: target_hosts
  tasks:
    - name: Import Child Playbook
      import_playbook: child.yml
```

**Child Playbook (`child.yml`):**
```yaml
---
- name: Child Playbook
  tasks:
    - name: Task 1
      # Task 1 details

    - name: Task 2
      # Task 2 details
```

In this case, when the parent playbook is executed, it will import the child playbook as a separate play, allowing you to control the order and inclusion of tasks more explicitly.

Note that the path to the child playbook should be relative to the location of the parent playbook or specified with an absolute path.

Using `include` or `import_playbook`, you can easily structure your Ansible playbooks by splitting them into reusable components, making your automation logic more modular and maintainable.


**more**

In Ansible, the `import` statement is used to include or import another playbook or task file into the current playbook. It allows you to modularize your playbook and reuse existing playbooks or task files. There are two types of imports in Ansible: `import_playbook` and `import_tasks`.

1. **import_playbook:**
The `import_playbook` statement is used to import and include another playbook into the current playbook. It allows you to execute the tasks defined in the imported playbook. Here's an example:

```yaml
---
- name: Main Playbook
  hosts: all
  tasks:
    - name: Task in Main Playbook
      debug:
        msg: "This is a task in the main playbook."

- name: Including Another Playbook
  hosts: all
  tasks:
    - import_playbook: path/to/another-playbook.yml
```

In this example, the `import_playbook` statement is used to include the tasks defined in the `another-playbook.yml` file into the main playbook. When the `import_playbook` statement is encountered, Ansible will execute the tasks defined in the imported playbook.

2. **import_tasks:**
The `import_tasks` statement is used to import and include another task file into the current playbook. It allows you to reuse tasks across multiple playbooks. Here's an example:

```yaml
---
- name: Main Playbook
  hosts: all
  tasks:
    - name: Task in Main Playbook
      debug:
        msg: "This is a task in the main playbook."

    - import_tasks: path/to/tasks-file.yml
```

In this example, the `import_tasks` statement is used to include the tasks defined in the `tasks-file.yml` file into the main playbook. When the `import_tasks` statement is encountered, Ansible will execute the tasks defined in the imported task file.

When using imports, it's important to note that imported playbooks or tasks will inherit the variable context and configuration of the calling playbook. This allows for modularization and reusability while maintaining the flexibility to customize the imported tasks based on the specific requirements of each playbook.

Imports provide a powerful way to organize and structure your Ansible playbooks by breaking them into smaller components. This promotes code reuse and maintainability of your automation codebase.