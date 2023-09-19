In Ansible, handlers are tasks that are triggered and executed only when notified by other tasks. They allow you to define actions that should be taken in response to changes in the state of your systems or infrastructure.

Handlers are typically used to restart services, reload configurations, or perform other actions that need to be executed only when a change has occurred. For example, if a configuration file is modified during the execution of a playbook, a handler can be defined to restart the associated service only if the file has changed.

Here's an example of how handlers are used in an Ansible playbook:

```yaml
---
- name: Example Playbook with Handlers
  hosts: webservers
  tasks:
    - name: Copy configuration file
      copy:
        src: app.conf
        dest: /etc/app.conf
      notify: Restart App Service

  handlers:
    - name: Restart App Service
      service:
        name: app_service
        state: restarted
```

In this example, we have a playbook that copies a configuration file (`app.conf`) to the target hosts. The `notify` directive is used to notify a handler named `Restart App Service` if the file is changed during the playbook execution.

The handler is defined in the `handlers` section of the playbook. It specifies a task that restarts the `app_service` using the `service` module with the `state: restarted` parameter.

Handlers are only triggered if they are notified by a task. In this case, when the `copy` task modifies the `app.conf` file, it triggers the associated handler, which then restarts the `app_service` on the target hosts.

To run a playbook that includes handlers, you can use the `ansible-playbook` command as usual:

```plaintext
ansible-playbook playbook.yml
```

Ansible ensures that the handlers are executed in the order they are defined, and they are executed only once, even if multiple tasks notify the same handler.

Handlers provide a way to control and manage the state of your systems or infrastructure based on changes that occur during playbook execution. They help ensure that necessary actions are taken only when required, improving the efficiency and reliability of your automation.