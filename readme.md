# Lab > Ansible with Docker

> Set up the environment with Ansible and Docker

## Setting up Docker

Use this [guide](https://docs.ansible.com/ansible/latest/collections/community/docker/docsite/scenario_guide.html) to configure ansible as a docker container.

Here are some resources that might help assist in standing up the [docker and ansible](https://www.simplilearn.com/tutorials/ansible-tutorial/what-is-ansible).

## Using [Playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html#working-with-playbooks)

Here are some [tips and tricks](https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html#playbooks-best-practices) for running ansible.

### Example Playbook

```yaml
---
- name: Update web servers
  hosts: webservers
  remote_user: root

  tasks:
    - name: Ensure apache is at the latest version
      ansible.builtin.yum:
        name: httpd
        state: latest
    - name: Write the apache config file
      ansible.builtin.template:
        src: /srv/httpd.j2
        dest: /etc/httpd.conf

- name: Update db servers
  hosts: databases
  remote_user: root

  tasks:
    - name: Ensure postgresql is at the latest version
      ansible.builtin.yum:
        name: postgresql
        state: latest
    - name: Ensure that postgresql is started
      ansible.builtin.service:
        name: postgresql
        state: started

```

### Running the Playbook

```bash
ansible-playbook playbook.yml -f 10
```

### Objectives

1. Run ansible using only Docker.
2. Create a simple ansible playbook
3. Run the playbook using the Docker environment
