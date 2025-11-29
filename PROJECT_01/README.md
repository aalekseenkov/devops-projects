# Test 99999999 Ansible Playbook with Docker

![Test Ansible Playbook with Docker](https://raw.githubusercontent.com/aalekseenkov/devops-projects/refs/heads/master/PROJECT_01/images/devops_project_01_01.jpg)  

Having some simple tests could solve our issues while we are developing playbooks, and provide some constant feedback about the playbooks' validity. But how do we test Ansible playbooks (other than lint them)?

> __Playbooks are just ordered instructions describing a desired state__

Still, they could be faulty - it's easy to make mistakes when we're trying to translate our desired configuration steps into Ansible tasks. We may mess up a task, forget a necessary parameter on a module, maybe we try to install something for which we forget to provide it's prerequisites. Preferably we want some tests which can run our playbooks against an ephemeral environment to see if they're well-runnable.

This is where docker comes into the picture. In docker we can test most of the things that we'd want to do with Ansible. Obviously for more complicated playbooks this might not be a good solution.

## How to Test Ansible Playbook
We should clone the project and **update templates** for our current task according all our requirements.
```
.
├── Dockerfile
├── ansible.cfg
├── playbook.yml
└── run-test.sh
```
The purpose of the files:
* **Dockerfile** - to configure our container according to the necessary conditions for the target host
* **ansible.cfg** - to control our configation of Ansible for the current test case
* **playbook.yml** - to place our test playbook
* **run-test.sh** - to manage all stages of our testing process

## Tips and Tricks
**To change permission for docker.sock:**  
```sudo chmod 666 /var/run/docker.sock```

**To verbose more or less information change -vvv in run-test.sh**  
```ansible-playbook -i "${TEMP_INVENTORY_FILE}" -vvv "${base_dir}/playbook.yml"```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMwNTc1MTczMSwtMTQyMTg3NjM4MSwxNz
g5NDgzNTcxLC01NDIxMTQ5ODYsMTc4OTQ4MzU3MSwtNTM4ODQ2
MDc0LDE3ODk0ODM1NzEsLTI3NzE2NTczN119
-->