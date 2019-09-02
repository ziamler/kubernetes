Role Name
=========

Kubernetes is an open source system for managing containerized applications across multiple hosts; providing basic mechanisms for deployment, maintenance, and scaling of applications.

Requirements
------------
Requires Docker; recommended role for Docker installation:Kubernets-Docker-Install.yml

Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

pod_net_cidr:10.244.0.0/16

Dependencies
------------
set ansible inventory like this

[master]
10.0.12.1

[node]
10.0.12.2

Example Playbook
----------------
---
- hosts: master,node
  remote_user: root
  roles:
    - role: k8s

- hosts: master
  remote_user: root
  vars_files:
  - roles/k8s/defaults/main.yml
  tasks:
  - import_tasks: roles/k8s/tasks/Kubernets-setup.yml

- hosts: node
  remote_user: root
  tasks:
   - import_tasks: roles/k8s/tasks/join_node.yml

License
-------

BSD

Author Information
------------------
Khushal Bisht
