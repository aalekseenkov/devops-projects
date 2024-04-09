# Test Ansible Playbook with Docker

![Test Ansible Playbook with Docker](/PROJECT_01/images/devops_project_01_01.jpg)

Having some simple tests could solve our issues while we are developing playbooks, and provide some constant feedback about the playbooks' validity. But how do we test Ansible playbooks (other than lint them)?

> __Playbooks are just ordered instructions describing a desired state__

Still, they could be faulty - it's easy to make mistakes when we're trying to translate our desired configuration steps into Ansible tasks. We may mess up a task, forget a necessary parameter on a module, maybe we try to install something for which we forget to provide it's prerequisites. Preferably we want some tests which can run our playbooks against an ephemeral environment to see if they're well-runnable.

This is where docker comes into the picture. In docker we can test most of the things that we'd want to do with Ansible. Obviously for more complicated playbooks this might not be a good solution.
